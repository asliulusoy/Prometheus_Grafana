# Prometheus

### Nedir?:
- ***Time series (Numeric) Database*** *Paralel bir şekilde birçok veri kaynağından, birçok türden verinin, birim t anında birbiriyle eşleştirilebilmesi.*
   - Kritik dataların tutulmaması gerekir,
   - Veri güvenliği açısından kalıcı data tutulması risklidir.
- ***Monitoring***
    - Basit bir arayüz veya güçlü APIlerle dışarı verilir. **(Grafana)**
    - Grafik veya chart oluşumunda farklı ürünler kullanılır.
- ***Opensource***
- ***Query***
    - **PromQL** sorgulama dili üzerinden Prometheus üzerinde tutulan veriler sorgulanabilir
- ***Alerting***
    - **Alert Manager Tool** kuralları (örneğin, sistem CPU'su 90% üzerine çıktığında bize mail atsın) tanımlanabilir.
- ***Storage***

### Ne değildir?:
- ***Loglama Platformu değildir.***
   - Geçmiş dataların toplanmasından ziyade anlık data önemlidir.
- ***Tracing Platformu değildir.***
   - Anlık veri takibi için doğru ürün değildir. **Open Zipkin** gibi tracing ürünleri daha faydalı olur.
- ***Kalıcı Storage değildir.***
   - Odak noktası veriyi tutmak, yedeklemek, güvenliğini sağlamak değildir.
- ***Clustering sağlamaz***
  - Farklı toollar kullanılarak oluşturulabilir.

  ![Prometheus Chart](https://blog.clearscale.com/wp-content/uploads/2022/08/Prometheus-1024x717.png)


# Grafana

- Görselleştirme amacıyla kullanılır.

  ![Grafana UI](https://grafana.com/media/products/cloud/grafana/grafana-dashboard-english.png)

# Exporters
- ***cAdvisor (Container Advisor)***
    - Docker container'da çalışan instance'ın metriclerini export eder.
- ***NodeExporter***
    - Docker container'ının metric'lerini export eder.
- ***JmxExporter***
    - Java process metriclerini, java internal metriclerini gönderir.
- ***MysqldExporter***
- ***AWS CloudWatchExporter***
- ***HAProxyExporter***
- ***Snmp Exporter***
    - Network montiroring tarafında kullanılır.
- ...


# Kurulum
- docker-compose.yml ve prometheus.yml dosyaları oluşturulur.

`docker-compose -f .\docker-compose.yml up` ile ayağa kaldırılır.
- localhost:9090 üzerinde Prometheus çalışır.
- localhost: 3000 üzerinde Grafana çalışır.

- Data Source eklenir
    - localhost:9090 yerine container name (prometheus-example:9090) kullanılır.
      
    ![prometheus_localhost](https://github.com/asliulusoy/Prometheus_Grafana/assets/132180090/9d5da18b-85ee-4764-840d-25fcbd8a6a3a)


    - Output:
      
    ![success_output](https://github.com/asliulusoy/Prometheus_Grafana/assets/132180090/c632410f-475b-434b-a510-00f306c9ce66)


- Prometheus üzerinde node_loader1 query testi:
  
![prometheus_nodeload1](https://github.com/asliulusoy/Prometheus_Grafana/assets/132180090/1a502a78-08f3-472b-bfe0-5e13e5a53677)


- Data Visualization için Grafana konfigüre edilir,
   - Grafana üzerinde node_loader1 query testi:
  
![grafana_nodeload1](https://github.com/asliulusoy/Prometheus_Grafana/assets/132180090/aefcf1b8-310b-4e17-b22c-d4e5b735d77f)
