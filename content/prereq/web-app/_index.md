
+++
title = "Running the Web App"
weight = 2
pre = "<b>2.2 </b>"
+++

___

1. Clone the current repository to your Cloud9 IDE
   
   ```bash
   git clone https://github.com/oconpa/facial_rekog.git
   ```
   
2. Move into the cloned directory and install all required packages. 

   ```bash
   cd facial_rekog/frontend
   npm install
   ```
   
3. Run the React application
   ```bash
   npm run start
   ```
   
4. Preview your Web Application
   
   After the app has compiled with warnings (Don't worry we will fix these along the way), click **Tools** in the toolbar up top, click **Preview** and finally click **Preview Running Application**. 
   Open the preview in another tab by clicking the arrow / box button on the right of the search bar. 

![Preview](/img/preview.png)

**You should see a basic web app in your browser! However, there is currently no functionality. Let's use AWS to fix this!**
