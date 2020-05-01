# locuszoom


https://genome.sph.umich.edu/wiki/LocusZoom_Standalone


(1) install python and R in linux system
(2) install new_fugue  and  plink for LD calculation
(3) download the full folder of locuszoom (including all data files with LD files) to drive, untar all files
(4) go to example and run  the Python script (with the txt file with p-vaule, with the exact format) to get locuszoom plot

Our system is in attie-vm:
/mnt/data/locuszoom

just go the example and use the Python script for analysis.
If change the path, go to conf folder and change the configure file.

to update mm10 to .db:
bin/lzupdate.py --build mm10 

using conf/m2z.config file to change your configuration

To run LocusZoom in remote server:
1. cd  to  examples
   in Attie-VM  using adminstor account
   $ sudo su
   $ ---password
   $ cd /mnt/data/locuszoom/examples
2. conduct shell to setup path for tabix for LD calculation 
      export PATH=$PATH:/mnt/data/locuszoom/tabix-0.2.6
3. upload gwas file to this folder
   this text file must have two columns,   MarkerName and P-value (column name should be exactly these two)   
4. edit python file to perform locuszoom
   to calculate LD, using mouse_vcf.py to do it   
   change   --refsnp  to your snp  and change --flank   to 200kb or 500kb as needed
   
5. conduct  ./mouse_vcf.py to draw plots
   ./mouse_vcf.py

To run LocusZoom in Parks's lab computer:

1. using VMware to login into Ubuntu system.
      username: parks  password:.....  (highly recommending using root access) 
         sudo su
2. mount sda3 , in terminal: 
      /mount -t ext4 /dev/sda3  /mnt/sda3
3. go to sda3 and locuszoom
      cd /mnt/sda3/locuszoom
4. change path 
   export PATH=$PATH:/mnt/sda3/locuszoom/tabix-0.2.6    Or  go to example using:   ./export.sh
5. go to example folder 
    cd example  
6. upload gwas file to this example directory for your analysis
   this text file must have two columns,   
      MarkerName and P-value (column name should be exactly these two, MarkerName and P-value can see example) 
7. edit python file to perform locuszoom to calculate LD, using mouse_vcf.py  
   change   --refsnp  to your snp  and change --flank   to 200kb or 500kb as needed
8. go to conf folder
   rm m2zfast.conf
   cp mouse.conf m2zfast.conf  (for human, using cp human.conf m2zfast.conf)
9. conduct  ./mouse_vcf.py to draw plots using following code
   ./mouse_vcf.py
   
warning: python2 is needed, python --version should come back to python 2
 
 


