FROM alpine
# Docs of env variables used for this image
# to test this locally just run
# docker build -t tmp_prover -f =(f envsubst < ./docker/prover/Dockerfile) .; docker run --rm  tmp_prover:latest
#ENV SUPPORTED_BLOCK_CHUNKS_SIZES $SUPPORTED_BLOCK_CHUNKS_SIZES
#ENV SUPPORTED_BLOCK_CHUNKS_SIZES_SETUP_POWERS $SUPPORTED_BLOCK_CHUNKS_SIZES_SETUP_POWERS
#ENV BLOCK_CHUNK_SIZES $BLOCK_CHUNK_SIZES
#ENV KEY_DIR $KEY_DIR
#ENV ACCOUNT_TREE_DEPTH $ACCOUNT_TREE_DEPTH
#ENV BALANCE_TREE_DEPTH $BALANCE_TREE_DEPTH
#ENV PROVER_SERVER_URL $PROVER_SERVER_URL
#ENV REQ_SERVER_TIMEOUT $REQ_SERVER_TIMEOUT
#ENV RUST_BACKTRACE $RUST_BACKTRACE
#ENV RUST_LOG $RUST_LOG
#ENV PROVER_DOWNLOAD_SETUP $PROVER_DOWNLOAD_SETUP
#ENV PROVER_SETUP_NETWORK_DIR $PROVER_SETUP_NETWORK_DIR
#ENV PROVER_PREPARE_DATA_INTERVAL $PROVER_PREPARE_DATA_INTERVAL
#ENV PROVER_HEARTBEAT_INTERVAL $PROVER_HEARTBEAT_INTERVAL
#ENV PROVER_CYCLE_WAIT $PROVER_CYCLE_WAIT
#ENV PROVER_GONE_TIMEOUT $PROVER_GONE_TIMEOUT
#ENV DOCKER_DUMMY_PROVER $DOCKER_DUMMY_PROVER
COPY target/x86_64-unknown-linux-musl/release/plonk_step_by_step_prover /bin/
COPY target/x86_64-unknown-linux-musl/release/dummy_prover /bin/
COPY docker/prover/prover-entry.sh /bin/
COPY bin/plonk-setup /bin/
COPY bin/verify-keys /bin/
COPY bin/utils.sh /bin/
COPY keys/packed /keys/packed
COPY contracts/build/ /contracts/build/
RUN apk add --no-cache axel curl bash

CMD ["prover-entry.sh"]
