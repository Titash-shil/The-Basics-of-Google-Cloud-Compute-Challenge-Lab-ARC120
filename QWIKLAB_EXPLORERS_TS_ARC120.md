# The Basics of Google Cloud Compute: Challenge Lab || [ARC120](https://www.cloudskillsboost.google/focuses/65384?parent=catalog) ||

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

* `Create a bucket` : from [here](https://console.cloud.google.com/storage/create-bucket?)

* For `Bucket name` check `TASK-1` of lab instruction!

---

### Run the following Commands in CloudShell

```
export ZONE=
```
```
gcloud compute instances create my-instance \
    --machine-type=e2-medium \
    --zone=$ZONE \
    --image-project=debian-cloud \
    --image-family=debian-11 \
    --boot-disk-size=10GB \
    --boot-disk-type=pd-balanced \
    --create-disk=size=100GB,type=pd-standard,mode=rw,device-name=additional-disk \
    --tags=http-server

gcloud compute disks create mydisk \
    --size=200GB \
    --zone=$ZONE

gcloud compute instances attach-disk my-instance \
    --disk=mydisk \
    --zone=$ZONE

sleep 15

cat > prepare_disk.sh <<'EOF_END'

sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx

EOF_END

gcloud compute scp prepare_disk.sh my-instance:/tmp --project=$DEVSHELL_PROJECT_ID --zone=$ZONE --quiet

gcloud compute ssh my-instance --project=$DEVSHELL_PROJECT_ID --zone=$ZONE --quiet --command="bash /tmp/prepare_disk.sh"
```

---

# Congratulations ..!!🎉  You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)
