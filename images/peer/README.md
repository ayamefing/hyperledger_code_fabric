## peer
生成 fabric-peer 镜像。

包括 Dockerfile.in 文件，内容为：

```sh
FROM hyperledger/fabric-runtime:_TAG_
ENV PEER_CFG_PATH /etc/hyperledger/fabric
RUN mkdir -p /var/hyperledger/db $PEER_CFG_PATH/msp/sampleconfig/signcerts $PEER_CFG_PATH/msp/sampleconfig/admincerts $PEER_CFG_PATH/msp/sampleconfig/keystore $PEER_CFG_PATH/msp/sampleconfig/cacerts
COPY payload/peer /usr/local/bin
COPY payload/core.yaml $PEER_CFG_PATH
COPY payload/msp/sampleconfig/signcerts/peer.pem $PEER_CFG_PATH/msp/sampleconfig/signcerts
COPY payload/msp/sampleconfig/admincerts/admincert.pem $PEER_CFG_PATH/msp/sampleconfig/admincerts
COPY payload/msp/sampleconfig/keystore/key.pem $PEER_CFG_PATH/msp/sampleconfig/keystore
COPY payload/msp/sampleconfig/cacerts/cacert.pem $PEER_CFG_PATH/msp/sampleconfig/cacerts
CMD peer node start
```