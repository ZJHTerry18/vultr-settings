# vultr-settings

## Install nginx
```sh
apt install nginx
sudo ufw app list
sudo ufw allow 'Nginx Full'
```

## For GDrive Download

## For Aws-cli Download
- Install aws-cli
```sh
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

- Set aws configurations
```sh
aws configure
# Then enter the AWS ID and AWS Key.
```

### Ego4D download
- Install prerequisites
```sh
git clone https://github.com/facebookresearch/Ego4d.git
cd Ego4d
pip install -r requirements.txt
pip install ego4d
```

- Upload a json file containing all the video_uids
- Run the download scripts
```sh
JSON='E4D_video_ids.json'
VIDEO_IDS=$(jq -r '.[]' $JSON)
OUTPUT='ego4d_data'

for video in $VIDEO_IDS; do
    echo "Downloading $video"
    ego4d --output_directory=$OUTPUT --dataset full_scale --video_uids $video -y
done
```
