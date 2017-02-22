---
title: "Convenciones de iostreams | Microsoft Docs"
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
  - "iostream (encabezado)"
  - "Biblioteca estándar de C++, iostreams"
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Convenciones de iostreams
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las conversiones admiten encabezados de iostreams entre el texto y los formularios codificados, y la entrada y salida a archivos externos:  
  
|||  
|-|-|  
|[\<fstream\>](../standard-library/fstream.md)|[\< iomanip \>](../standard-library/iomanip.md)|  
|[\<ios\>](../standard-library/ios.md)|[\<iosfwd\>](../standard-library/iosfwd.md)|  
|[\<iostream\>](../standard-library/iostream.md)|[\< istream \>](../standard-library/istream.md)|  
|[\<ostream\>](../standard-library/ostream.md)|[\<sstream\>](../standard-library/sstream.md)|  
|[\< streambuf \>](../standard-library/streambuf.md)|[\<strstream\>](../standard-library/strstream.md)|  
  
 El uso más simple de iostreams sólo requiere incluya el encabezado [\<iostream\>](../standard-library/iostream.md).  Después puede extraer valores de [cin](../Topic/cin.md) o de [wcin](../Topic/wcin.md) para leer la entrada estándar.  Las reglas para ello se describen en la clase [basic\_istream \(Clase\)](../standard-library/basic-istream-class.md).  También puede insertar valores a [cout](../Topic/cout.md) o a [wcout](../Topic/wcout.md) para escribir la salida estándar.  Las reglas para ello se describen en la clase [basic\_ostream \(Clase\)](../standard-library/basic-ostream-class.md).  El común del control de formato a ambos extractores e insertors es administrado por la clase [basic\_ios \(Clase\)](../standard-library/basic-ios-class.md).  Manipulación de esta información de formato SO pretexto de extraer e insertar objetos es el estado de varios manipuladores.  
  
 Puede realizar las mismas operaciones de iostreams en los archivos que abra por nombre, mediante las clases declaradas en [\<fstream\>](../standard-library/fstream.md).  Para convertir entre iostreams y los objetos de la clase [basic\_string \(Clase\)](../standard-library/basic-string-class.md), utilice las clases declaradas en [\<sstream\>](../standard-library/sstream.md).  Para hacer lo mismo con cadenas de C, utilice las clases declaradas en [\<strstream\>](../standard-library/strstream.md).  
  
 Los encabezados restantes proporcionan servicios de soporte técnico, normalmente de interés directo sólo a la mayoría de los usuarios avanzados de las clases de iostreams.  
  
## Vea también  
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)