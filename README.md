# farmBeat

### This is is a walkthrough on how to upload a fake data to elasticserch and view it in Kibana.

1. install elasticserch and Kibana and run them in your terminal (port 9200 and 5601)
2. go to [json-generator](http://www.json-generator.com)
.
3. Paste your schema.
```
[
  '{{repeat(3000)}}',
  {
    cow_id: '{{index()}}',
    infeccion_mamaria: '{{bool()}}',
    parto: '{{integer(1, 6)}}',
    rendimiento: '{{floating(25.0, 31.9)}}',
    nombre: '{{firstName()}}',
    establo: '{{random("establo A", "establo B", "establo C")}}',
    nutricion: '{{random("Mezcla 1", "Mezcla 2", "Mezcla 3")}}',
    genetica: '{{random("Holstein", "Pardo Suizo", "Cebú")}}'

  }

]
```
4. Download the file and save it in your working directory.
5. Follow the instructions of this [repo](https://github.com/mradamlacey/json-to-es-bulk)

###### We need to use the aforementioned repo because elastic search receives data bulk kind of form. In other words, if we try to curl it using the format from [json-generator](http://www.json-generator.com) we will receive an error ( "status" : 500 or   "status" : 400). So we need to format it before we upload it.

6. After following the latter repo instructions we should be able to continue. Go to
this [localhost/settings/IndexPatterns/AddNew](http://localhost:5601/app/kibana#/management/kibana/index/?_g=()) and uncheck "Index contains time-based events"

7. If you run this command ```curl 'localhost:9200/_cat/indices?v'``` in your terminal you should be able to see that there is an index called ```true```  with a docs count of ```3000```.

8. Fill Index name or pattern with ```true``` and create it!

######If you can see the true index page we are ready to go. Now all the info. is properly loaded in elasticserch hence is ready to be used in kibana!

9. Go to kibana [Visualize your data](https://www.elastic.co/guide/en/kibana/current/tutorial-visualizing.html#tutorial-visualizing)

10. Pie graph

![1](https://github.com/shekodn/farmBeat/blob/master/Screenshots/1.png)
