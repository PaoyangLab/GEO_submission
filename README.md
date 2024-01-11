# Submit Data to GEO


**G**ene **E**xpression **O**mnibus (GEO) is a public genomics data repository that facilitates data submissions adhering to the MIAME standards. It accepts both array-based and sequence-based data and provides tools to assist users in querying and downloading gene expression profiles for experiments and studies.


Essentially, the original sequencing data from articles is often required to be submitted to this database.


## Uploading your dataset
### Step1: Preparing your submission

Visit the [ NCBI homepage](https://www.ncbi.nlm.nih.gov/) and navigate to **Submit** page.

![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_1.png)

Scroll down to **Other Toools** and locate the **GEO** box.

![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_2.png)

Select the data type that you want to upload (e.g., NGS data) and click the **Submit high-throughput sequencing**.

![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_3.png)


Then, select **Raw data files**.



Run an md5 check for data integrity during transfer, the md5 should also be provided to GEO.

```bash
md5sum *.fastq.gz > md5.txt
```

### Step2: Submit your data
There are two steps for GEO submission. 
GEO submission involves two steps. Firstly, transfer all your files to the GEO server. Navigate to **Transfer Files**.

![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_4.png)

Login to NCBI and GEO would then assign the path for data uploading in their **step 1.** protocal, as well as the FTP username & password in **step 2.**.
> use your ouwn accont and fill in the PI information as a **Invesgetor**.
> ![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_6.png)

![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_8.png)
![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_9.png)


Multiple options are available for dataset upload. Here, I recommend using SFTP for transferring data from local to another server.


```bash
### In your local terminal, login to GEO FTP server
sftp geoftp@host_address # host_address is in step2.
# entre the password GEO provided

### Create your own floder that GEO provided
mkdir upload/the_folder_name_GEO_provided

### Create your a new folder for this submission
mkdir geo_submmsion_Jan04

### Go to the GEO FTP server selected folder 
cd upload/the_folder_name_GEO_proveid/geo_submmsion_Jan04

### Go to the local folder that contain your data
lcd ur_local_data_file

### Copy the data and md5 to the GEO FTP server
put *fastq.gz
put md5.txt

### Check tha md5
md5sum -c md5.txt

```


### Step3: Fill out the Metadata form
Download the latest Metadata form and complete all the required (labeled in **) cells. 
> An example form is downloaded on the date 2024.01.04.

![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_10.png)
![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_11.png)


### Step4: Submit your data
After finishing data transfer, go to the next box, **Upload metadata**,nd upload the selected subfolder, metadata sheet, and choose a release date. 

![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_13.png)


Finally, click **Submit**! Then you will receive an email if the upload is successful.

![](https://github.com/beritlin/NGS_analyses/blob/main/Figure/GEO_12.png)
