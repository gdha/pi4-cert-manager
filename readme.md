# Pi4 Cert-manager yaml file

To download the ARM version of cert-manager yaml file to install or upgrade the kubernetes pod:

```bash
VER=$(curl -s "https://github.com/jetstack/cert-manager/releases/latest" | cut -d\" -f2 | awk -F '/' '{print $NF}')

curl -sL \
https://github.com/jetstack/cert-manager/releases/download/${VER}/cert-manager.yaml |\
sed -r 's/(image:.*):(v.*)$/\1-arm:\2/g' > cert-manager-arm.yaml
```

Finally, we can install or upgrade our cert-manager pods with the command:

```bash
# install
$ kubectl install -f cert-manager-arm.yaml

# upgrade
$ kubectl replace -f cert-manager-arm.yaml
```

### References

[1] [cert-manager GitHub pages](https://github.com/jetstack/cert-manager)
