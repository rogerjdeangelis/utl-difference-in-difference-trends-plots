# utl-difference-in-difference-trends-plots
Difference-in-difference-trends-plot

    Difference-in-difference-trends-plot                                                                                   
                                                                                                                           
    Problem;                                                                                                               
      Change in Workforce Participation after the Earned Tax Credi Bill was passed.                                        
      The bill was designed to help low-income families with children,                                                     
                                                                                                                           
    You should easily be able to convert this to SAS code.                                                                 
                                                                                                                           
    github                                                                                                                 
    https://tinyurl.com/y4bam5w5                                                                                           
    https://github.com/rogerjdeangelis/utl-difference-in-difference-trends-plots                                           
                                                                                                                           
    See                                                                                                                    
    https://dhicks.github.io/2018-10-10-did/                                                                               
                                                                                                                           
    SAS Forum                                                                                                              
    https://tinyurl.com/y4mbwggk                                                                                           
    https://communities.sas.com/t5/Statistical-Procedures/Difference-in-difference-trends-plot/m-p/570489                  
                                                                                                                           
                                                                                                                           
    In year 4 the Earned Income Tax Credit was passed EITC                                                                 
                                                                                                                           
    Dummies                                                                                                                
                                                                                                                           
    post3 =  (year >= 4)     * 1 after 1993 Earned Tax Credit(EITC) was passed                                             
    anykids = (children >= 1)                                                                                              
                                                                                                                           
    *_                   _                                                                                                 
    (_)_ __  _ __  _   _| |_                                                                                               
    | | '_ \| '_ \| | | | __|                                                                                              
    | | | | | |_) | |_| | |_                                                                                               
    |_|_| |_| .__/ \__,_|\__|                                                                                              
            |_|                                                                                                            
    ;                                                                                                                      
                                                                                                                           
    SD1.HAVE total obs=2,760                                                                                               
                                                                                                                           
      Workforce                                coded as 1-6                                                                
      participation   year >= 4   children >=1  1991-1996                                                                  
                                                                                                                           
          WORK          POST3        ANYKIDS        YR                                                                     
                                                                                                                           
            1             0             1            1                                                                     
            0             0             0            1                                                                     
            1             0             1            1                                                                     
            1             0             0            1                                                                     
            1             0             0            1                                                                     
            1             0             1            1                                                                     
            1             0             0            1                                                                     
            0             0             0            1                                                                     
            0             0             1            1                                                                     
            1             0             1            1                                                                     
            0             0             0            1                                                                     
            1             0             1            1                                                                     
                                                                                                                           
      ...                                                                                                                  
                                                                                                                           
    options validvarname=upcase;                                                                                           
    libname sd1 "d:/sd1";                                                                                                  
    data sd1.have;                                                                                                         
    retain work post3 anykids;                                                                                             
     input yr 1. POST3 1. ANYKIDS 1.  work 1. @@;                                                                          
    cards4;                                                                                                                
    10111000101110011001101110011000101010111000101110101001200120112001201020102000                                       
    20112010200120113001300030103011301030013001301030103001300030004111410141004111                                       
    41004110411141114100510151105101510051015100511051105100511151105110610061106100                                       
    61016100610061006100611010011010101110111001101010011000101110111011100010011010                                       
    10101010101110011011101010001011100010111011101110111001100110111001101010111010                                       
    10011000101010011010100010001010101010101011101010001010100110011001100010101011                                       
    10001010100010111010101010001010100010011010100110011010101010011010100010001000                                       
    10101010101110001000101110001001101010101010101010111010101010001010100010101011                                       
    10001010101010101011100110111010101010101001100110001011100010001000100110111011                                       
    10011011100010111011101110101011100010101000100110001011100110111001100010011001                                       
    10001001101010101001101010111000101110001010100110111011101010001011100010011001                                       
    10101001100110111010100010011011100010111010101110001010101110011001101010101010                                       
    10101001100110101011101110001010101010111000100010101001101110101011101110101010                                       
    10101011101110101010101010001001100110101011100010111000101010111001100110101001                                       
    10001001100010101011101010111000100010101001101110001000101110011001101110111010                                       
    10011001100110111011101110101011101110111010100010101011100110011001100010111011                                       
    10111000101110111011101110111001100110111010101110011001101010011001100110111011                                       
    10001010100110101010100110101010101010111010101110111010100010111011101110001000                                       
    10111011101010101010100010111010101010101011101010101010101010011000101010111010                                       
    10001011101110101011101010111011101010001001100110101010101110101000101110001011                                       
    10101000101110011001100010011001101010001010101010011000101110101010101110011010                                       
    10111011100110101010101110101011100110011001100110001010101010001010101110111010                                       
    10011010100110101000101110101001100110111001100010001001101010101011101110001010                                       
    10001001100010101001101110011011101010111010101010011000101010111001101110011001                                       
    10111001100110111001101010101010101110001010101010101011101010001010101010011010                                       
    10101011101010111011100110111001100010101001101110001000101110011010100110101001                                       
    10101010101110001010100110111001101010011011101110111001100110111001100110011010                                       
    10011011101010001001101110011001101010111010101010111001100110111001100110101010                                       
    10011011100110111011100110001000101010101011101110111010101110001011101010011011                                       
    10011010101110011001101010001011201020102010201120102000200020102000201120002001                                       
    20102011200120102010201020102010201020102010200120102000201020012001201020112010                                       
    20102011200020112010200020012001201120002011201020102010201020102010201120012010                                       
    20112001200120002001200120002000201120102010201120102001201020012000201120102010                                       
    20102010200020102001200020012000200120112011200020102000200020112000200020012001                                       
    20112001200120002001201020112001201120102010200020112010200120102010201020002010                                       
    20002000201020102001200120012001200120012001200120112010201120102000200020112010                                       
    20002000201120112011200120012000201120012000200120012000201120102001201020102011                                       
    20012000201020102000201020102001201120102010201120002010201020002001200020112010                                       
    20102011201120012011201120102011201020012001200120002011201020012000200120012010                                       
    20112010201120002011200120012010201120102000201020012001201120102000201120012011                                       
    20002011201120102001200120112011201020002001200020112010201020102011200120002001                                       
    20012011200120112000201020012000201120012001201120112011200020102001200020112010                                       
    20012001201020112010200120102011201020102001201120002011200020012010201120112001                                       
    20112010201120112000200120102011200020102010200020102011200120102001200020012010                                       
    20002000201020002011201020002011201120012010201120112011201020112011201120112011                                       
    20112011201020102010200020102000200120112011201120012011200120112010201020002010                                       
    20102011201120112010201120002010201020112010200120112001200120012010201020012010                                       
    20002001201120012011200020102011201020012010201020112001201120112011200020102001                                       
    20102001201020112010201020102010201120112010200120112011200120102010200120012010                                       
    20112001201020002010200020112001201120002011201020012000201120112000201020012000                                       
    20012010201120002010201020102011201120002000201020012010201120102010200120112010                                       
    20012001200120002000201020102010201120102010201120012001201020002011201020012011                                       
    20112011201120102000200120102010201020102010200020012010200020102010201120012001                                       
    20013010301030013001301030103011301030103000300030113010300030103001300030003001                                       
    30103001300030103001301030013010301030103001301030113000300030003010300130013000                                       
    30103011301030113000301030013001301030103001301030103010301030103011301030013000                                       
    30113010300030103010301030003011300030103000301030013001301130003010301030013011                                       
    30003011301030113001300130113011300130103001301030113010301030103010301030113010                                       
    30003010300030113010300130003010301030003011300030003000300030103001301130113000                                       
    30003000301030113001300130003001300030013001301030103001301130113000301130003010                                       
    30013010301130013000300130103010301030103000301130003000300030013010301030113000                                       
    30103011300030013001300030103001300130113010301130113010301030013001300130013011                                       
    30113001301030103001301130113001300130003010301030103001300030113000301130003001                                       
    30103001301130013001301130113000300130013001300030103001300030113001301030103001                                       
    30113010301030103000301130013010301130103011301130003010300030113001301130113011                                       
    30113011301130003001301130103011300130113001300030013001300030013010300030013001                                       
    30003001301130103010300130103001301030103001301030113011300030113010301130113001                                       
    30013001300130103010301030113010300130113001300130113000300130013010301030013011                                       
    30003000300130003000300030013010301130003001301030113011301130113000301030103001                                       
    30013010300030113011300030003010301030003000301130113000300030003000300030103011                                       
    30013011301130113010301130113010301130113011301030003010301130103010301030113000                                       
    30013011300130003000301030013000300130103011301130003001301030013010301030103010                                       
    30113011301130113010300130113001301030113001301030013011300030013010300130003011                                       
    30113000301130003010301030103010301130103000301130113001300030013011301030103011                                       
    30113010301030003011300130013010300130103001301030113001301130103010301130113011                                       
    30013010301130113000301030113000300130013010300130103010301130113001300130113010                                       
    30013010301030103000301030013001300130003000300130103010301130003010301130103000                                       
    41014101411041114110411141014110411041014101411041014110410041004111411041114100                                       
    41014101410141104101410041004101410141104110411141014110411141104111411141004111                                       
    41004110411141114100411141104110411041104101411041104111411041004110411141004100                                       
    41004100410141104100411041014101411041014101410041104100411041114110410041104100                                       
    41114101411041104101411041114110410141014110410041014111411141104100411141004111                                       
    41014110411141014111410141004110411041114110411141014110411141004100411141104110                                       
    41114100411141014110411041114101411041104111410141104101410041004111411041014100                                       
    41004101410041114100410141104110410041104101411041114110410141114101411041004110                                       
    41114111410041104100410041104100410141004110411141004100411141114101410041004111                                       
    41114101410141014111411141014101411041104110410041114110411041014101411141104111                                       
    41104110410141014101411041014111411141004110410141104101410141104100411041114100                                       
    41114110411141014101410041014110410041114110410141014110410041014101411041114101                                       
    41114110411141014111410041014101410141104111411041004111411141104110411141014101                                       
    41114100411141114110411041104111410141114101410141004100410041014110410041104110                                       
    41114111411141114110411041014111410041114100411041104101411141014110411141104100                                       
    41114111410141014110410141114100411141104111410141114101411041104100411041014111                                       
    41014101410141014101411141114111411041014101411141114100411141014110411141014110                                       
    41014101410141114110410041104111411141114100411041114110410041104111411141114110                                       
    41104101411041114100411141104101411141114111410141014101410141014100410141114101                                       
    41114101410141014110411141004101411141104110410141114100411141104101411141004111                                       
    41114110410141014101411041114111411141114101411041114101410141014110411041014110                                       
    41004100411041004100410041004110411041104110411141114111410041014101410051105100                                       
    51115111510051115100511151015111511051005101511051005110511051005110510151005100                                       
    51105110511051015101510051005110510051105111510051005110510051015100511051015110                                       
    51105111510051115111510151105100510051015110511051105101510151115100510151005101                                       
    51115101511051005101510151015100511151005101511151005101510051015110510151115111                                       
    51005101511151005110511051005100510151015101510151005111510151015110510051015101                                       
    51015100511151115110510151005101510151105110510151005110511151115110510151115101                                       
    51015111510051015101510151015100510151015101510051105101510151115101510051105101                                       
    51115111510051005111511151005110511151015111511151015110511151115111511151005101                                       
    51115100510151115111510151015101510051015101510151105101511151015110510151005101                                       
    51115111510151115111510151005100511151015101511051105100511051115111511051115101                                       
    51015111510051105101511151005111510051005100510151105101511051005101510051115110                                       
    51115111510151105110511051105110510051105100510051005110511051115100511151115111                                       
    51105111511051015111510151105111510151115100511051015101511151015100511151005111                                       
    51115110511151105110511151015101511151115100511051115100511151115101511051015110                                       
    51015111511051115110510051105111510051115110511151005100511051115110511151105111                                       
    51115101510051105101510051115110511051105110510051005101510151115101511151105100                                       
    51115101510051015110510151105110511051005111511051005111511151115111511051105101                                       
    51105100511051105111510151005111510051115111510151015110511151105111510051105111                                       
    51015111511051015100511051105101511051115110510151115110510051105101511051115101                                       
    61116101611061006101610061116111611161106111611161116111611161106110610061016110                                       
    61106110610061116110611161106110610061106110611061106110611061106100611161116110                                       
    61116101611061106110611061006111611061106111610161116110610161016110611061106110                                       
    61006111610061016101610061106100610161016101610161016101611161116110610061016101                                       
    61006101610061016100610061016100611061016110611061006100611061016101611161006101                                       
    61016110610161016101610061006101610161006110611161016110610061106111611061016110                                       
    61016101611061106101611161116100611161006111610161006101610161116100611161116100                                       
    61016110610061116100610161106101610061116100611161116110610061016111610161016101                                       
    61116110611061106100611061016111611161016110610161116101610161016101610161116101                                       
    61006111611161116110610061016100610061016111611161116100610161116110611161116111                                       
    61006101610161106100611161106101611161006110611061006100610161016101610061006111                                       
    61116100611061006101611161106101611161116100611161016110610161016111611161106101                                       
    61116101610161106110611161106111610061116111611061106111611061116111611061006101                                       
    61016111610161006101611161016101610161116100610061116101610161006101610161116100                                       
    61006100611061006110610161116111610161006101611161116110610161006111611061106101                                       
    61006110610061116111611061106110611061116110610161116101611061016101611161116110                                       
    61016110611161116111610161016101611061116110610061116101610161006111610161106100                                       
    61016111610061016111611161116101611161106110611161116110611161106111611161016101                                       
    61006101610061016111611161116110611061016101611061106110611161116111610161116100                                       
    6111610161116111611161016101                                                                                           
    ;;;;                                                                                                                   
    run;quit;                                                                                                              
                                                                                                                           
    *            _               _                                                                                         
      ___  _   _| |_ _ __  _   _| |_                                                                                       
     / _ \| | | | __| '_ \| | | | __|                                                                                      
    | (_) | |_| | |_| |_) | |_| | |_                                                                                       
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                      
                    |_|                                                                                                    
    ;                                                                                                                      
                                                                                                                           
    Workforce                                                                                                              
    Paticipation             Bill Passed                                                                                   
                                ^                                                                                          
          |                     |                                                                                          
          |                    /* 0                                                                                        
     0.60 +                   / |\                                                                                         
          |* 0----*          /  | \                                                                                        
          |        \0       /   |  \      O *  No children                                                                 
          |         \      /    |   \    /                                                                                 
          |          \    /     |    \  /                                                                                  
     0.55 +           \  / 0    |      * 0                                                                                 
          |             *       |           1-*  One or more                                                               
          |                     |         /      childen                                                                   
          |                     |        /                                                                                 
          |                     |       /                                                                                  
     0.50 +                     |   _  * 1                                                                                 
          |                     * 1                                                                                        
          |* 1                / |      Note the increase                                                                   
          |                  /  |      from 1994 to 1996                                                                   
          |    \            /   |      for families with                                                                   
     0.45 +     \          /    |      children                                                                            
          |       * 1 ---* 1    |                                                                                          
          |                     |                                                                                          
          |                     |                                                                                          
          |                     |                                                                                          
     0.40 +                     |                                                                                          
          |                     |                                                                                          
          -+------+------+------+------+------+-                                                                           
           1      2      3      4      5      6                                                                            
                                                                                                                           
                            YR                                                                                             
                                                                                                                           
                                                                                                                           
                              Estimate Std. Error    t value      Pr(>|t|)                                                 
                                                                                                                           
     (Intercept)            0.57165354 0.01973071 28.9727803 2.955713e-161                                                 
     ANYKIDSTRUE           -0.11451069 0.02591953 -4.4179301  1.035141e-05                                                 
     POST3TRUE              0.00838088 0.02854443  0.2936082  7.690795e-01                                                 
                                                                                                                           
                            **********                                                                                     
     ANYKIDSTRUE:POST3TRUE  0.04514699 0.03839459  1.1758686  2.397494e-01                                                 
                            **********                                                                                     
                                                                                                                           
    This indicates that the Earned Tax Credit increased workforce participation                                            
    by about 5% among families with at least 1 child.                                                                      
                                                                                                                           
    Note my result is not significant, but I had only about 20% of the data.                                               
                                                                                                                           
    *                                                                                                                      
     _ __  _ __ ___   ___ ___  ___ ___                                                                                     
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                    
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                    
    | .__/|_|  \___/ \___\___||___/___/                                                                                    
    |_|                                                                                                                    
    ;                                                                                                                      
                                                                                                                           
                                                                                                                           
    * Trend plot                                                                                                           
                                                                                                                           
    proc summary data=sd1.have mean nway;                                                                                  
    class yr anykids;                                                                                                      
    var work;                                                                                                              
    output out=havSum mean=work;                                                                                           
    run;quit;                                                                                                              
                                                                                                                           
    options ls=64 ps=32;                                                                                                   
    proc plot data=havsum(rename=work=w123456789012345678901234);;                                                         
      plot w123456789012345678901234*yr='*' $ anykids / href=4;                                                            
    run;quit;                                                                                                              
                                                                                                                           
    * Regression analysis;                                                                                                 
                                                                                                                           
    %utl_submit_r64('                                                                                                      
    library(dplyr);                                                                                                        
    library(haven);                                                                                                        
    library(ggplot2);                                                                                                      
    library(SASxport);                                                                                                     
    library(data.table);                                                                                                   
    have <- haven::read_sas("d:/sd1/have.sas7bdat");                                                                       
    head(have);                                                                                                            
    png(file="d:/png/trend.png");                                                                                          
    have$ANYKIDS=as.logical(have$ANYKIDS);                                                                                 
    have$POST3=as.logical(have$POST3);                                                                                     
    model = lm(WORK ~ ANYKIDS*POST3, data = have);                                                                         
    want<-summary(model)[[4]];                                                                                             
    want<-as.data.frame(capture.output(want));                                                                             
    want[] <- lapply(want, function(x) if(is.factor(x)) as.character(x) else x);                                           
    write.xport(want,file="d:/xpt/want.xpt");                                                                              
    ');                                                                                                                    
                                                                                                                           
                                                                                                                           
    libname xpt xport "d:/xpt/want.xpt";                                                                                   
    data want;                                                                                                             
      set xpt.want;                                                                                                        
    run;quit;                                                                                                              
    libname xpt clear;                                                                                                     
                                                                                                                           
    proc print data=want;                                                                                                  
    run;quit;                                                                                                              
                                                                                                                           
                                                                                                                           
                                                                                                                           
