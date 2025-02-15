# CSR Approver

```
helm install kubelet-csr-approver kubelet-csr-approver/kubelet-csr-approver -n kube-system \
  --set providerRegex='^node.*' \
  --set providerIpPrefixes='192.168.0.0/24' \
  --set bypassDnsResolution='true'

```