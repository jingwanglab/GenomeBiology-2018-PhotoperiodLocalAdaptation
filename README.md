# PhotoperiodLocalAdaptation
Scripts for Wang et al. (2018) "A major locus controls local adaptation and adaptive life history variation in a perennial plant". Genome Biology, 19, 72. https://genomebiology.biomedcentral.com/articles/10.1186/s13059-018-1444-y

<h2>Documentation of Scripts</h2>

<b>1. Sequencing quality checking, read mapping and post-mapping filtering</b>

        Picard_markduplicates_SwAsp.sh - Use Picard to correct for artifacts of PCR duplication

        QualityControl.sh - Use Trimmomatic v0.30 and FastQC to do sequence quality checking

        realign.sh - Use GATK to do read realignment around indels

        runBWA_mem_asp201.SwAsp.sh - Use BWA-MEM to do read mapping

    
<b>2. SNP and genotype calling</b>

        HaplotypeCaller_mem_tremula.sh - Use GATK to do SNP calling

        snpEff.gatk.sh - Use snpEff to annotate the SNPs

        vcf_to_maf.sh vcf2maf.pl - Use perl script to map each variant to only one of all possible gene isoforms

<b>3. Relatedness, population structure and isolation-by-distance</b>

        eigen_pop_genetics.sh - Use smartpca program in EIGENSOFT to perform PCA analysis

        fst_matrix.R - create the matrix of Fst estimates

        Isolation_by_distance.R - create the matrix of geographic distance
        
        mantel.R - Mantel test

        plink_prunedLD.sh - Use PLINK to generate Linkage-disequilibrium(LD)-trimmed SNP sets
        
        SwAsp.IBD.plot.R - plot Isolation-by-distance

<b>4. Screening for SNPs associated with local adaptation</b>

        env_PC.error_bar.R - Relationship between the environmental PC1 scores and the number of days with degree higher than 5
       
        GEMMA.lmm.noPC.budset.sh - Use GEMMA to do GWAS for budset

        Ekebo_Savar_budset.as - Use Asreml to estimate the genetic values of bud set
         
        LEA.K1.R LEA.K2.R LEA.K3.R - use a latent factor mixed-effect model (LFMM) implemented in the R package LEA to detect SNPs associated with first environmental PC, with the latent factors (K) from 1 to 3.
         
        LEA_zscore.94samples.R - Transform the z-scores from LFMM results to p-values


        PCAdapt.SwAsp94.R - PCAadapt test

        pcadapt_fst_cor.R - The relationship between PCadapt results and Fst values

        pca_corr_env.R - PCA analysis for the environment dat

        Figure2 - scripts for recreating Figure 2

            chr10.gemma.ld_Dprime.R - calculate LD and colorise points relative to tthe top SNP in PtFT2
            
            excute_manhanttan.sh - shell script for manhattan plots
            
            FT2.gemma.ld_Dprime.R - plot associations and colorise according to LD for the PtFT2 SNPs
            
            legend.col.R - plot legend
            
            manhanttan_plot.R - manhattan plots (modified from https://cran.r-project.org/web/packages/qqman/index.html)
            
            manhanttan.3methods.R - plot manhattan plots and qqplots and combine for three types of analyses (PCAdapt, LFMM, GWAS)
            
            scaffold_likely_wrong.txt - scaffolds that are likely missasembled and therefore exluded from the plots

<b>5. Genotype imputation</b>

        Beagle_comparison.sh - Create several missing genotypes for simulation

        createFile_imputate.R - Create imputation files with different level of missing values

        Create_simu_missing_file.sh - Tor simulate by BEAGLE and calculate accuracy

        define_ancestral.SwAsp.pseudo_chr.sh - Use BEAGLE to do genotype imputation and also define ancestal and derived allele based on the sequences of outgroup species of P.tremuloides and P.trichocarpa

        impute_accuracy_beagle_vcf.pl - Calculate the imputation accuracy by each sample and SNP

        impute_evaluate.R - Evaluate the imputation accuracy


<b>6. Positive selection</b>

        ABCinference.R - Script for performing Approximate Bayesian Computation (ABC) to jointly estimate s (the strength of selection on the beneficial mutation causing the sweep) and T (the time since the beneficial allele fixed). Script modified from original provided by Ormond et al (2016) at http://jjensenlab.org/wp-content/uploads/2016/02/ABC_inference.zip
        
        angsd_SFS_SwAsp.all.sh - Use ANGSD to estimate the genetic diversity in specific groups of populations

        caviar.chr10.sh caviar.z-score.R - Run CAVIAR on specific region of Chr10

        chr10_genome.sig.angsd_tP_tajD.group_plot.R - Compare the genetic diversity between chr10 region and genome-wide levels

        chr10_genome.sig.fst.group_plot.R - Compare Fst between chr10 region and genome-wide levels

        chr10_genome.sig.h12.group_plot.R - Compare H12 and H2/H1 between chr10 region and genome-wide levels

        chr10_genome.sig.sweepfinder2.group_plot.R - Compare CLR between chr10 region and genome-wide levels

        chr10_genome.sig.ihs_nsl.R - Compare iHS and nSL values between chr10 region and genome-wide levels

        ehh.plot.sh colormap.plotting.R - Create EHH plot

        genome_wide.summary.compare.sh - Use vcftools, selscan and H12 test to perform a set of selection tests across the genome

        ms2sf2.pl - Convert msms output to input format for SweepFinder2

        plink.ldheatmap.sh LDheatmap.R - Use PLINK to calculate LD across SNPs

        run_sweep_sim.sg - Simulate independent selective sweep events using the coalescent simulation program msms and analyse the results using SweepFinder2 to assess region affected by sweep

        select.chr10.summary.sh - Use vcftools, selscan and H12 test to perform a set of selection tests on the specific region (~700kbp) on Chr10

        sweepfinder2.FT2paper.sh - Run SweepFinder2 to detect selection signals
