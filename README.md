# CBT388
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 388 is from David B. Cole and contains his operator       *   FILE 388
//*     commands scheduling facility.  An upgraded version of       *   FILE 388
//*     this code is available from his web site - below:           *   FILE 388
//*                                                                 *   FILE 388
//*            see   schedrun.zip                                   *   FILE 388
//*                                                                 *   FILE 388
//*    Dave Cole has updated most of his contributions, and         *   FILE 388
//*    they are available for direct download from his web          *   FILE 388
//*    site at www.colesoft.com.  The following list of             *   FILE 388
//*    his software is currently available there:                   *   FILE 388
//*                                                                 *   FILE 388
//*         Cole Software LLC's File Upload/Download Area           *   FILE 388
//*                                                                 *   FILE 388
//*       The following shareware is available for download         *   FILE 388
//*                                                                 *   FILE 388
//*      Filename   Platform            Description                 *   FILE 388
//*                                                                 *   FILE 388
//*    asm2zap.zip   z/OS      A utility for converting an          *   FILE 388
//*                            assembly listing into SUPERZAP       *   FILE 388
//*                            cards.                               *   FILE 388
//*                                                                 *   FILE 388
//*    blksptrk.zip  z/OS      A TSO command that computes and      *   FILE 388
//*                            displays track capacities for any    *   FILE 388
//*                            IBM DASD device for any BLKSIZE,     *   FILE 388
//*                            with or without key fields.          *   FILE 388
//*                                                                 *   FILE 388
//*    macros.zip    z/OS      A set of Assembler/390 macros        *   FILE 388
//*                            needed for assembling the various    *   FILE 388
//*                            programs available from Cole         *   FILE 388
//*                            Software LLC.                        *   FILE 388
//*                                                                 *   FILE 388
//*    schedrun.zip  z/OS      A set of MVS programs for            *   FILE 388
//*                            scheduling the execution of System   *   FILE 388
//*                            Operator Commands on an interval     *   FILE 388
//*                            or calander basis. Can be used to    *   FILE 388
//*                            control production scheduling.       *   FILE 388
//*                                                                 *   FILE 388
//*    xrefasm.zip   z/OS      A pair of programs for producing     *   FILE 388
//*                            master cross-reference listings      *   FILE 388
//*                            for multi-assembly programs.         *   FILE 388
//*                                                                 *   FILE 388
//*              Colesoft Marketing, Inc.                           *   FILE 388
//*              414 3rd ST. NE                                     *   FILE 388
//*              Charlottesville, VA 22902 USA                      *   FILE 388
//*              540-456-8210                                       *   FILE 388
//*              www.colesoft.com                                   *   FILE 388
//*              email:  dbcole@gmail.com                           *   FILE 388
//*                                                                 *   FILE 388
//*     FOR ADDITIONAL INFORMATION PLEASE SEE THE MEMBER CALLED     *   FILE 388
//*     $$DOC AND READ THE FOLLOWING :                              *   FILE 388
//*                                                                 *   FILE 388
//*     A PROGRAM HAS BEEN WRITTEN TO PRINT OUT THE AUTOMATIC       *   FILE 388
//*     SCHEDULING FACILITY FILE BY MAY & SPEH AND IS CONTAINED     *   FILE 388
//*     IN FILE 422 OF THIS TAPE                                    *   FILE 388
//*                                                                 *   FILE 388
//*     THE MACROS NEEDED FOR THIS SYSTEM ARE CONTAINED IN          *   FILE 388
//*     FILE 408 OF THIS TAPE                                       *   FILE 388
//*                                                                 *   FILE 388
//*     THE SCHEDULE FACILITY MAKES IT POSSIBLE TO SCHEDULE THE     *   FILE 388
//*     AUTOMATIC EXECUTION OF ANY OPERATOR COMMAND AT ANY TIME     *   FILE 388
//*     OF DAY ON ANY DATE.  THE EXECUTION OF THE COMMAND CAN       *   FILE 388
//*     BE REPEATED ACCORDING TO ANY OF A LARGE VARIETY OF          *   FILE 388
//*     DAILY, WEEKLY, MONTHLY, AND/OR YEARLY REPEAT CYCLES.        *   FILE 388
//*     (SEE THE ACCOMPANYING TSO HELP FILE FOR DETAILS).           *   FILE 388
//*                                                                 *   FILE 388
//*     THE SCHEDULE FACILITY SUPPORTS AN OVERRIDE CAPABILITY       *   FILE 388
//*     WHEREBY PARTICULAR SETS OF PERIODICALLY SCHEDULED           *   FILE 388
//*     COMMANDS CAN BE OVERRIDDEN ON SELECTED DATES (SUCH AS       *   FILE 388
//*     HOLIDAYS) WITH ANOTHER SET OF COMMANDS TO BE EXECUTED       *   FILE 388
//*     INSTEAD.  SUCH OVERRIDES CAN BE DEFINED EVEN YEARS IN       *   FILE 388
//*     ADVANCE, IF DESIRED.                                        *   FILE 388
//*                                                                 *   FILE 388
//*     THE SCHEDULE FACILITY PERMITS THE DEFINITION OF A           *   FILE 388
//*     "WINDOW" PERIOD (DEFINED SEPARATELY FOR EACH SCHEDULED      *   FILE 388
//*     AUTOMATIC COMMAND) WHEREBY:                                 *   FILE 388
//*                                                                 *   FILE 388
//*        - IF THE SYSTEM IS DOWN AT THE TIME THAT A COMMAND       *   FILE 388
//*          IS SCHEDULED TO BE EXECUTED,                           *   FILE 388
//*                                                                 *   FILE 388
//*        - BUT IF THE SYSTEM COMES UP ANY TIME DURING THE         *   FILE 388
//*          SPECIFIED "WINDOW PERIOD" FOLLOWING THE COMMAND'S      *   FILE 388
//*          SCHEDULED TIME,                                        *   FILE 388
//*                                                                 *   FILE 388
//*        - THEN THAT COMMAND WILL BE EXECUTED ANYWAY.             *   FILE 388
//*                                                                 *   FILE 388
//*     THUS THE EXECUTION OF IMPORTANT COMMANDS WON'T BE           *   FILE 388
//*     MISSED JUST BECAUSE THE SYSTEM WASN'T UP IN TIME.           *   FILE 388
//*                                                                 *   FILE 388
//*     IN JES2 "MULTI-ACCESS SPOOL" CONFIGURATIONS, THE            *   FILE 388
//*     SCHEDULE FACILITY'S VSAM DATA BASE CAN BE SHARED            *   FILE 388
//*     BETWEEN MULTIPLE SYSTEMS, AND OPERATOR COMMANDS CAN BE      *   FILE 388
//*     SCHEDULED TO EXECUTE ON EITHER ONE OR THE OTHER (OR         *   FILE 388
//*     "ANY") OF THE ATTACHED CPUS.                                *   FILE 388
//*                                                                 *   FILE 388
//*     THE SCHEDULE FACILITY CAN MAINTAIN A LOG FILE WHERE IT      *   FILE 388
//*     RECORDS A TIMESTAMPED COPY OF ALL OPERATOR COMMANDS         *   FILE 388
//*     THAT IT ISSUES.                                             *   FILE 388
//*                                                                 *   FILE 388
//*     THE SCHEDULE FACILITY IS DESIGNED TO EXECUTE IN A JES2      *   FILE 388
//*     ENVIRONMENT.  IF YOU WISH TO USE IT IN A JES3 SYSTEM,       *   FILE 388
//*     THEN YOU MUST MAKE SUITABLE MODIFICATIONS TO THE            *   FILE 388
//*     FACILITY'S SOURCE CODE.                                     *   FILE 388
//*                                                                 *   FILE 388
```
