FROM public.ecr.aws/g5p1t6g5/alpine:3.13.5
LABEL maintainer="Glen Stummer <glen@glen.dev>"

SHELL ["/bin/ash", "-eo", "pipefail", "-c"]
RUN apk add --no-cache --virtual .build-deps \
    zip \
    curl &&\
    curl -L "$(curl -Ls https://api.github.com/repos/terraform-linters/tflint/releases/latest | grep -o -E "https://.+?_linux_amd64.zip")" -o tflint.zip &&\
    unzip tflint.zip &&\
    rm tflint.zip &&\
    mv tflint /usr/local/bin/ &&\
    apk del --purge .build-deps

ENTRYPOINT ["/usr/local/bin/tflint"]
CMD ["."]
