# utl-scraping-a-single-indirect-html-reference-using-python-beautiful-soup-and-request-packages
Scraping a single indirect html reference using python beautiful soup and request packages   
    Scraping a single indirect html reference using python beautiful soup and request packages                                                         
                                                                                                                                                       
    The OP wants to get just the closing stock price for Stock STOXX                                                                                   
                                                                                                                                                       
    github                                                                                                                                             
    https://tinyurl.com/y9x9fyff                                                                                                                       
    https://github.com/rogerjdeangelis/utl-scraping-a-single-indirect-html-reference-using-python-beautiful-soup-and-request-packages                  
                                                                                                                                                       
    The value of STOOX at market cloles is not in the html source but is pulled from an ouside data source.                                            
                                                                                                                                                       
    SOAPBOX ON                                                                                                                                         
      The problem with R and Python is getting data into and out.                                                                                      
      It took me a ling time to get the number 372.5 in a string.                                                                                      
      Python is worse then R especially the datatype "object".                                                                                         
    SOAPBOX OFF;                                                                                                                                       
                                                                                                                                                       
                                                                                                                                                       
    StackOverflow                                                                                                                                      
    https://tinyurl.com/yc2lx4af                                                                                                                       
    https://stackoverflow.com/questions/62246411/webscrape-data-python-beautifulsoup4                                                                  
                                                                                                                                                       
    Andrej Kesely profile                                                                                                                              
    https://stackoverflow.com/users/10035985/andrej-kesely                                                                                             
                                                                                                                                                       
    *_                   _                                                                                                                             
    (_)_ __  _ __  _   _| |_                                                                                                                           
    | | '_ \| '_ \| | | | __|                                                                                                                          
    | | | | | |_) | |_| | |_                                                                                                                           
    |_|_| |_| .__/ \__,_|\__|                                                                                                                          
            |_|                                                                                                                                        
    ;                                                                                                                                                  
                                                                                                                                                       
    https://tradingeconomics.com/stoxx:ind                                                                                                             
                                                                                                                                                       
    The key tag is  '#market_last'                                                                                                                     
                                                                                                                                                       
    function UpdateMarketTick() {                                                                                                                      
        socket.on('tick', function (t) {                                                                                                               
            if (t.state && t.state == 'closed') {                                                                                                      
                console.log('market is closed');                                                                                                       
            }                                                                                                                                          
            var s = t.s;                                                                                                                               
                                                                                                                                                       
            if (!s || s.toLowerCase() != symbol.toLowerCase()) {                                                                                       
                return;                                                                                                                                
            }                                                                                                                                          
            //console.log('s', s, symbol)                                                                                                              
            var triangle = t.nch > 0 ? '<span class="market-positive-image"></span>'                                                                   
               : t.nch < 0 ? '<span class="market-negative-image"></span>' : '';                                                                       
            //$("#market-price").html(t.p + ' ' + triangle + ' ' + t.nch + ' ' + t.pch + '%');                                                         
                                                                                                                                                       
            $('#market_last').html(t.b || t.p);                                                                                                        
            $('#market_daily_chg').html(t.nch);                                                                                                        
            $('#market_daily_Pchg').html('(' + t.pch + '%)');                                                                                          
                                                                                                                                                       
            if (t.nch > 0) { //market_chg_arrow                                                                                                        
                $('#market_chg_arrow').attr('class', 'market-positive-image');                                                                         
                $('#market_daily_chg').css({                                                                                                           
                    color: '#8ecf61'                                                                                                                   
                });                                                                                                                                    
                $('#market_daily_Pchg').css({                                                                                                          
                    color: '#8ecf61'                                                                                                                   
                });                                                                                                                                    
            } else {                                                                                                                                   
                $('#market_chg_arrow').attr('class', 'market-negative-image');                                                                         
                $('#market_daily_chg').css({                                                                                                           
                    color: '#ed3b3b'                                                                                                                   
                });                                                                                                                                    
                $('#market_daily_Pchg').css({                                                                                                          
                    color: '#ed3b3b'                                                                                                                   
                });                                                                                                                                    
            }                                                                                                                                          
                                                                                                                                                       
        });                                                                                                                                            
                                                                                                                                                       
    *            _               _                                                                                                                     
      ___  _   _| |_ _ __  _   _| |_                                                                                                                   
     / _ \| | | | __| '_ \| | | | __|                                                                                                                  
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                                   
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                                  
                    |_|                                                                                                                                
    ;                                                                                                                                                  
                                                                                                                                                       
    %put &=fromPy;                                                                                                                                     
                                                                                                                                                       
       FROMPY = 375.32                                                                                                                                 
                                                                                                                                                       
    *                                                                                                                                                  
     _ __  _ __ ___   ___ ___  ___ ___                                                                                                                 
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                                                
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                                                
    | .__/|_|  \___/ \___\___||___/___/                                                                                                                
    |_|                                                                                                                                                
    ;                                                                                                                                                  
                                                                                                                                                       
                                                                                                                                                       
    %symdel fromPy / nowarn;                                                                                                                           
                                                                                                                                                       
    %utl_submit_py64_38('                                                                                                                              
    import bs4;                                                                                                                                        
    import io;                                                                                                                                         
    import requests;                                                                                                                                   
    import pyperclip;                                                                                                                                  
    url="https://tradingeconomics.com/stoxx:ind";                                                                                                      
    soup=bs4.BeautifulSoup(requests.get(url).content, "html.parser");                                                                                  
    output = io.StringIO();                                                                                                                            
    print(soup.select_one("#market_last").text,file=output,end="");                                                                                    
    output = output.getvalue();                                                                                                                        
    pyperclip.copy(output);                                                                                                                            
    output.close();                                                                                                                                    
    ',return=fromPy);                                                                                                                                  
                                                                                                                                                       
    %put &=frompy;                                                                                                                                     
                                                                                                                                                       
                                                                                                                                                       
