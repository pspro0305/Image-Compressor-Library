# Image-Compressor-Library
Image Compression using C# Library in any .net platform project.


Steps to add assembly 
1. First add the dll file ImageCompression.dll in the reference folder
2. Add assembly refrence  using ImageCompression;
3. set Stream strm = imgInp.InputStream;
4 Invoke class object as CompressByPrakhar Cp = new CompressByPrakhar();
5. call method to compress file  Cp.ReduceImageSize(0.5, strm, path); 
6. where => scaleFactor to be compressed i.e. 0.5 , add IO strem i.e. strm , add path where file to save.
7. Upload image and compare both file size , customize the scalefactor from 0.5 to any of your choice, enjoy.

// Test Code 
// Happy Coding 


string prepath = "~/Content/Uploads";
            string path = "";
            var uploadUrl = Server.MapPath(prepath);
            Stream strm = imgInp.InputStream;
            string extension = System.IO.Path.GetExtension(Request.Files["imgInp"].FileName);
            if (extension.ToLower() == ".jpeg" || extension.ToLower() == ".jpg")
            {
                if (imgInp.ContentLength > 0)
                {
                    imgInp = Request.Files["imgInp"];
                    string Name = DateTime.Now.Ticks + "_Ptest" + ".jpg";  //reduce after test
                    string pathtosave = prepath + "/" + Name;
                    path = uploadUrl + "/" + Name;
                    Model.ImagePath = pathtosave;
                    CompressByPrakhar Cp = new CompressByPrakhar();  
                    Cp.ReduceImageSize(0.5, strm, path);              
                }
                else
                {
                    TempData["Message"] = "Please Upload Photo !";
                }
            }
