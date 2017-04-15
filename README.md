# farmBeat

This is is a walkthrough on how to upload a fake data to elasticserch and
view it in Kibana.

1. install elasticserch and Kibana.
2. go to http://www.json-generator.com.
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
5. Follow the instructions of:
   https://github.com/mradamlacey/json-to-es-bulk

##### We need to use the aforementioned repo because elastic search receives data bulk kind of form. In other words, if we try to curl it using the format that http://www.json-generator.com we will receive an error (  "status" : 500 or   "status" : 400). So we need to format it before we upload it.
