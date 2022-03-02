

# Netbeans github entegrasyonunda "Incorrect credentials" hatasının çözümü:

- Github hesabında sağ tarafta profile -> settings tıklayınız
- Sol taraftaki menüden "Developer settings" tıklayınız
- Menüden "Personel Access Tokens" tıklayınız
- Token geçerlilik süresini girdikten sonra "scope" başlığı altında "repo" işaretleyiniz
- "Generate Token" düğmesine tıklayınız
- Üretilen token bilgisini kopyalayıp netbeans deki parola kısmına yapıştırınız


# Netbeans HelloWorld uygulamasında build.xml de hatası
   **Hata 1**: Glassfish 6.2.5 sunucu logunda "org.apache.catalina.LifecycleException: java.lang.ClassNotFoundException: javax.faces.webapp.FacesServlet" hatası alıyorum.
    
   **Çözüm**:HelloWorld uygulamasında web.xml içeriği aşağıdaki gibi olmalıdır. 
   
   1. web-app değiştirilmelidir.
   2. javax yerine jakarta kullanılmalıdır.  
  
          <?xml version="1.0" encoding="UTF-8"?>
          <web-app xmlns="jakarta.ee/xml/ns/jakartaee" xmlns:xsi="w3.org/2001/XMLSchema-instance" xsi:schemaLocation="jakarta.ee/xml/ns/jakartaee jakarta.ee/xml/ns/jakartaee/web-app_5_0.xsd" version="5.0" metadata-complete="true">
              <context-param>
                  <param-name>jakarta.faces.PROJECT_STAGE</param-name>
                  <param-value>Development</param-value>
              </context-param>
              <servlet>
                  <servlet-name>Faces Servlet</servlet-name>
                  <servlet-class>jakarta.faces.webapp.FacesServlet</servlet-class>
                  <load-on-startup>1</load-on-startup>
              </servlet>
              <servlet-mapping>
                  <servlet-name>Faces Servlet</servlet-name>
                  <url-pattern>/faces/*</url-pattern>
              </servlet-mapping>
              <session-config>
                  <session-timeout>
                      30
                  </session-timeout>
              </session-config>
              <welcome-file-list>
                  <welcome-file>faces/index.xhtml</welcome-file>
              </welcome-file-list>
          </web-app>
