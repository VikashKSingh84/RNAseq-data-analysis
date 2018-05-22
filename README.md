############################# RNAseq-data-analysis#############################################################
# bowtie2-build genome_assembly.fasta bt2_gemome_assembly.fasta
# /opt/tophat-2.0.6.Linux_x86_64/tophat -p 10 --library-type fr-unstranded --transcriptome-index bt2_nrCDS_mRNA -G nrCDS_gff bt2_genome_assembly.fasta Run26_s_6_sequence_filtered 
# samtools view accepted_hits.bam | cut -f1 | sort | uniq | wc -l
# samtools view tophat_out/accepted_hits.bam | fgrep -wc "NH:i:1"
# samtools faidx ../../chickpea_final_15_02.fasta
# sort -k 1,1 ../../chickpea_final_15_02.fasta.fai > ../../chickpea_final_15_02.fasta.fai.s
# samtools view accepted_hits.bam > accepted_hits.sam
# samtools view -h -S -t ../../chickpea_final_15_02.fasta.fai.s -o accepted_hits_s.sam accepted_hits.sam
# cufflinks accepted_hits_s.sam -o cufflink_output -p 10 -g ../../Ca_gff -b /userdata/vikash/GenomeAnnotData/unMasked2/chickpea_final_15_02.fasta -u
# gffread transcripts.gtf -w transcripts.fa -g /userdata/vikash/GenomeAnnotData/unMasked2/chickpea_final_15_02.fasta
# cuffmerge -o cuffmerge_output -g Ca_gff -s chickpea_final_15_02.fasta -p 10 cufflink_assembly_GTF_list.txt
# gffread merged.gtf -w merged.fa -g /userdata/vikash/GenomeAnnotData/unMasked2/chickpea_final_15_02.fasta
# cuffdiff -o cuffdiff_output -b -u -N -p 10 -L MF2,SAM2,YP2 cuffmerge_output/merged.gtf MF2/tophat_out/accepted_hits_s.sam SAM2/tophat_out/accepted_hits_s.sam YP2/tophat_out/accepted_hits_s.sam
