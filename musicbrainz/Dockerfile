FROM ubuntu:jammy

RUN apt-get update && \
    apt-get install --no-install-recommends -qy \
        make \
        git \
        ca-certificates \
        cpanminus \
        gettext \
        g++ \
        # Needed for Cache in DB_File
        libdb-dev \
        libexpat1-dev \
        libicu-dev \
        liblocal-lib-perl \
        libpq-dev \
        libssl-dev \
        # Needed for XML::LibXML
        libxml2-dev \
        # Needed for Unicode::ICU::Collator
        pkg-config \
        # Needed for XML:LibXML
        zlib1g-dev \
    && rm -rf /var/lib/apt/lists/*

# Get database tools from musicbrainz-server
RUN git clone --depth=1 https://github.com/metabrainz/musicbrainz-server.git musicbrainz-server

WORKDIR /musicbrainz-server

RUN eval "$(perl -Mlocal::lib)" \
    && cpanm --installdeps --notest .

CMD ["sleep", "infinity"]