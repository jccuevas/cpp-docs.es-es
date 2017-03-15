---
title: "Rutas de b&#250;squeda en reglas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reglas de inferencia en NMAKE"
  - "reglas, inferencia"
  - "rutas de búsqueda en reglas de inferencia en NMAKE"
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Rutas de b&#250;squeda en reglas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

```  
{frompath}.fromext{topath}.toext:  
   commands  
```  
  
## Comentarios  
 Una regla de inferencia se aplica a una dependencia sólo si las rutas de acceso especificadas en la dependencia coinciden exactamente con las rutas de acceso de la regla de inferencia.  El directorio del dependiente se especifica en *frompath* y el directorio de destino en *topath*; no se permiten espacios.  Sólo se especifica una ruta de acceso para cada extensión.  Una ruta de accesos en una extensión requiere una ruta de acceso en la otra.  Para especificar el directorio actual, se ha de utilizar un punto \(.\) o llaves vacías \({ }\).  Las macros pueden representar *frompath* y *topath*; se las llama durante el preprocesamiento.  
  
## Ejemplo  
  
### Código  
  
```  
{dbi\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUDBI) $<  
  
{ilstore\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{misc\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{misc\}.c{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{msf\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{bsc\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{mre\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{namesrvr\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{src\cvr\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
```  
  
## Vea también  
 [Definir una regla](../build/defining-a-rule.md)