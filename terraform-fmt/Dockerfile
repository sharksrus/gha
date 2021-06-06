FROM public.ecr.aws/g5p1t6g5/alpine:3.13.5
LABEL maintainer="Glen Stummer <glen@glen.dev>"

ENV TERRAFORM_VERSION=0.15.5
ENV TERRAFORM_SHA256SUM=3b144499e08c245a8039027eb2b84c0495e119f57d79e8fb605864bb48897a7d

COPY entrypoint.sh /entrypoint.sh

RUN apk add --no-cache --virtual .build-deps \
    zip \
    curl &&\
    curl https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip > terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    echo "${TERRAFORM_SHA256SUM}  terraform_${TERRAFORM_VERSION}_linux_amd64.zip" > terraform_${TERRAFORM_VERSION}_SHA256SUMS && \
    sha256sum -c terraform_${TERRAFORM_VERSION}_SHA256SUMS && \
    unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    mv terraform /bin/terraform && \
    rm -f terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    chmod +x /entrypoint.sh && \
    apk del --purge .build-deps

ENTRYPOINT [ "/entrypoint.sh" ]
CMD ["."]
