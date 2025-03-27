# iot_03
IOT_ASIGMENT_03
AWS IoT Environmental Station

This project is a virtual environmental monitoring system that simulates sensor data (temperature, humidity, CO₂) and publishes it to AWS IoT Core using the MQTT protocol. It is designed as a solution for CIS600 Spring 2025 Assignment 3.

✅ Features

Simulates 3 virtual sensors: Temperature, Humidity, and CO₂

Publishes data every 15 seconds to AWS IoT Core

Uses secure TLS connection with X.509 certificates

Designed to be extended with AWS IoT Analytics for data processing and querying

📦 Project Structure

.
├── virtual_station_aws.py        # Virtual sensor script
├── AmazonRootCA1.pem             # AWS IoT Root CA
├── device-certificate.pem.crt    # Your device certificate
├── private.pem.key               # Your private key
├── README.md                     # This file

🔧 Prerequisites

AWS Account

Python 3.8+

Install Dependencies:

pip install paho-mqtt

Download Certificates from AWS IoT Console:

AmazonRootCA1.pem

Device certificate (e.g., device-certificate.pem.crt)

Private key (e.g., private.pem.key)

🚀 Setup Instructions

1. Create an AWS IoT Thing

Go to AWS IoT > Manage > Things > Create

Name your thing (e.g., station_001)

Auto-generate certificate and download it

Attach a policy (see below)

2. Create and Attach Policy

Go to Secure > Policies > Create

Use this JSON in "Advanced Mode":

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "iot:*",
      "Resource": "*"
    }
  ]
}

Attach the policy to your certificate

3. Find Your AWS IoT Endpoint

Go to Settings in AWS IoT Console

Copy your Endpoint URL and replace it in the Python script

📡 Running the Virtual Station

python virtual_station_aws.py

You should see output like:

Publishing: { 'station_id': 'station_001', 'temperature': 21.5, 'humidity': 48.7, 'co2': 950, 'timestamp': '2025-03-26 17:45:00' }

🔍 Viewing Data in AWS

Go to AWS IoT Console

Open MQTT test client

Subscribe to:

iot/environment/#

You’ll see incoming messages in real-time.

📈 Optional: AWS IoT Analytics

You can connect your channel/pipeline/datastore in IoT Analytics to:

Store data

Run SQL queries

Create scheduled dataset refreshes

Integrate with Jupyter Notebooks for analysis

👨‍💻 Author

Ameya Jajulwar (ANJAJULW@SYR.EDU)


