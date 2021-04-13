FROM alpine:3.13.4
LABEL Glen Stummer <glen@glen.dev>

ENV TERRAFORM_VERSION=0.14.10
ENV TERRAFORM_SHA256SUM=45d4a12ca7b5c52983f43837d696f45c5ed9ebe536d6b44104f2edb2e1a39894

RUN apk add --no-cache --virtual .build-deps \
    zip~=3.0 \
    curl~=7.74.0 &&\
    curl https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip > terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    echo "${TERRAFORM_SHA256SUM}  terraform_${TERRAFORM_VERSION}_linux_amd64.zip" > terraform_${TERRAFORM_VERSION}_SHA256SUMS && \
    sha256sum -c terraform_${TERRAFORM_VERSION}_SHA256SUMS && \
    unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    mv terraform /bin/terraform && \
    rm -f terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    apk del --purge .build-deps

ENTRYPOINT [ "/bin/terraform" ]

CMD ["terraform fmt -check -diff"]