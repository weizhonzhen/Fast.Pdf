# FastHtmlToPdf
Fast.pdf create pdf by wkhtmltopdf
      

nuget url: https://www.nuget.org/packages/Fast.HtmlToPdf
          
          
          
           using(var pdf = HtmlToPdf.Instance())
           {
                var path = string.Format("{0}\\print.htm", System.AppDomain.CurrentDomain.BaseDirectory);
                var html = System.IO.File.ReadAllText(path);
                var doc = new PdfDocument();
            
                doc.DisplayFooter = true;
                doc.Footer.Url = "http://" + HttpContext.Request.Host.Value + "/home/footer";
                doc.Footer.Spacing = 10;

                doc.DisplayHeader = true;
                doc.Header.Url = "http://" + HttpContext.Request.Host.Value + "/home/header";
                doc.Header.Spacing = 10;
                                
                doc.MarginBottom = 50;
                doc.MarginTop = 50;
                        
                return File(pdf.Convert(doc, html), "application/pdf");
            }
            
            page html must be include  "<!DOCTYPE html>"
