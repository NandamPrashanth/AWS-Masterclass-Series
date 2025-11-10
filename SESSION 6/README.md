# SESSION 6

## 1.Introduction to EBS Volumes

### What is EBS?

**Amazon Elastic Block Store (EBS)** provides persistent, high-performance block storage for EC2 instances. Think of it as a virtual hard drive that you can attach to your cloud server.

### Key Characteristics:

- **Durable and Persistent**: Data remains intact even after instance termination (unless the "delete on termination" flag is enabled).
- **Attachable**: You can attach multiple volumes to a single instance.
- **Types**: gp3, gp2 (SSD), io2/io1 (Provisioned IOPS), st1, sc1 (HDD)
- **Snapshot Support**: Back up volumes using snapshots.
- **Region-Specific**: Volumes exist in a specific Availability Zone.

## 2.Attaching and Detaching EBS Volumes

### Attaching a Volume

1. Go to **EC2 Dashboard > Volumes**.
2. Click **Create Volume**.
3. Choose type, size, and AZ (must match EC2 instance AZ).
4. After creation, select the volume and click **Actions > Attach Volume**.
5. Choose your EC2 instance and provide a device name (e.g., `/dev/xvdf` for Linux or `xvdf` for Windows).
6. Click **Attach**.

### Detaching a Volume

1. Stop all read/write operations on the volume (important to avoid data corruption).
2. In the **Volumes** section, select your volume.
3. Click **Actions > Detach Volume**.
4. Wait for detachment before deleting or re-attaching.


## **For Linux**


| Step | Command                           | Description                       |
| ---- | --------------------------------- | --------------------------------- |
| 1    | `lsblk`                           | List all attached storage devices |
| 2    | `sudo fdisk -l`                   | View detailed disk partition info |
| 3    | `sudo file -s /dev/nvme1n1`       | Check existing file system        |
| 4    | `sudo mkfs -t xfs /dev/nvme1n1`   | Create new XFS file system        |
| 5    | `sudo file -s /dev/nvme1n1`       | Verify file system creation       |
| 6    | `sudo mkdir /mydata`              | Create mount point directory      |
| 7    | `sudo mount /dev/nvme1n1 /mydata` | Mount the EBS volume              |
| 8    | `df -h`                           | Check available and mounted disks |

And after taking the snapshot and creating a volume for it, follow the below commands

| Step | Command                           | Description                       |
| ---- | --------------------------------- | --------------------------------- |
| 1    | `lsblk`                           | List all attached storage devices |
| 2    | `sudo fdisk -l`                   | View detailed disk partition info |
| 3    | `sudo file -s /dev/nvme1n1`       | Check existing file system        |
| 4    | `sudo mkdir /mydata`              | Create mount point directory      |
| 5    | `sudo mount /dev/nvme1n1 /mydata` | Mount the EBS volume              |



## **For Windows**

# Create a New Volume (For Unallocated Disks)

- Right-click the *Unknown Disk* and select **Initialize Disk**.

If the disk shows **Unallocated space**:
- Right-click on the **Unallocated area** → **New Simple Volume**.
- Follow the **New Simple Volume Wizard**:
1. Specify volume size (use full size).
2. Assign a drive letter (e.g., `E:`).
3. Choose **NTFS** file system and set a **Volume Label** (optional).
- Click **Finish** to create and format the new volume.

