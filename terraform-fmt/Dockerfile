FROM public.ecr.aws/g5p1t6g5/alpine:3.13.5
LABEL maintainer="Glen Stummer <glen@glen.dev>"

ENV TERRAFORM_VERSION=0.15.4
ENV TERRAFORM_SHA256SUM=ddf9b409599b8c3b44d4e7c080da9a106befc1ff9e53b57364622720114e325c

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
