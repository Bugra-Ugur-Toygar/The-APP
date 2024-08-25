# The-APP
Ilk adımda node.js express kütüphanesini VS code’a kurdum ve GPT yardımıyla hello world çıktısını dönen kodu çıkarttım.  

Ikinci(2.) adımda Dockerfile oluşturdum burada “FROM node:14 sürümünü seçtim- çalışma dizini olarak WORKDIR /app i ayarladım- package jsonı koyternerina kopyaladım COPY package*.json ./-  RUN npm install ile gerekli olan bağımlılıkları indirmesini sağladım. 

-COPY . . - 

EXPOSE 3001 –3000 portu ödevi ilk yapışımda sorun çıkarttı başka bir yerde çalıştığı için o yüzden 3001 kullandım” 

CMD ["node", "app.js"]- 

Üçüncü(3.) adımda bu yazdıklarımın imajını oluşturup test ettim. 

docker build -t my-web-app . Ile imajımı oluşturdum ve docker run -p 3001:3001 my-web-app  ile uygulamayı çalıştırıp,  portu dışarı açtım. 

Dördüncü(4.) adım 

Docker Hub’a imajımı yükledim, docker tag my-web-app bugraugurtoygar/my-web-app:latest - docker push bugraugurtoygar/my-web-app:latest 

Beşinci(5.) adım ve altıncı(6.) adımda 

K8s deployment.yaml dosyası ve service-yaml dosyası oluşturdum ve kubectl apply -f deployment.yaml  ile kubectl apply -f service.yaml  kodlarını çalıstırdım. Böylelikle uygulamanın yönetimi ve erişimini sağlamış oldum, fakat bu kısım biraz uğraştırdı çünkü birkaç hata aldım. En sonunda, test başarılı bir şekilde çalıştı. 

K8s replicaset kullanarak pod sayısını 1’den 3’e çıkarttım ve bunu kubectl get pods ile test ettim.  

Son olarak ingress controller ekleyip çalıştırmayı denedim fakat ip adresi kısımlarında “none” yazdığı için devam edemedim.
