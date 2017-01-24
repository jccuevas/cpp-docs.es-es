---
title: "Flujos de entrada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "datos [C++], leer en secuencia de entrada"
  - "objetos de flujo de entrada"
  - "flujos de entrada"
  - "leer datos [C++], en secuencias de entrada"
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
caps.latest.revision: 11
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Flujos de entrada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objeto del flujo de entrada es un origen de bytes.  Las tres clases más importantes del flujo de entrada son [istream](http://msdn.microsoft.com/es-es/6801779e-260e-416d-b4ec-fef5ff1b2371), [ifstream](../Topic/ifstream.md), y [istringstream](../Topic/istringstream.md).  
  
 La clase de `istream` es más apropiado para la entrada secuencial del modo de texto.  Puede configurar objetos de clase `istream` para la operación almacenado en búfer o inseparada.  Toda la funcionalidad de la clase base, `ios`, se incluye en `istream`.  Se construirá raramente objetos de clase `istream`.  En su lugar, utilizará normalmente el objeto predefinido de `cin` , que es realmente un objeto de la clase [ostream](../standard-library/ostream.md).  En algunos casos, puede asignar `cin` a otros objetos de secuencia después de inicio del programa.  
  
 La clase de `ifstream` admite la entrada del archivo de disco.  Si necesita un archivo de disco de entrada \- solo, cree un objeto de la clase `ifstream`.  Puede especificar el binario o datos del modo de texto.  Si especifica un nombre de archivo en el constructor, el archivo se abre automáticamente cuando se construye el objeto.  Si no, puede utilizar la función de `open` después de invocar el constructor predeterminado.  Muchas opciones de formato y funciones miembro se aplican a los objetos de `ifstream` .  Toda la funcionalidad de las clases base `ios` y `istream` se incluye en `ifstream`.  
  
 Como la función de biblioteca `sscanf_s`, la clase de `istringstream` admite cadenas de en\- memoria.  Para extraer datos de una matriz de caracteres que tenga un terminador nulo, asigna e inicialice la cadena, se crea un objeto de la clase `istringstream`.  
  
## En esta sección  
 [Construir objetos de flujo de entrada](../standard-library/constructing-input-stream-objects.md)  
  
 [Usar operadores de extracción](../standard-library/using-extraction-operators.md)  
  
 [Comprobar errores de extracción](../standard-library/testing-for-extraction-errors.md)  
  
 [Manipuladores de flujos de entrada](../standard-library/input-stream-manipulators.md)  
  
 [Funciones de miembro de flujo de entrada](../standard-library/input-stream-member-functions.md)  
  
 [Sobrecargar el operador \>\> para las clases propias](../standard-library/overloading-the-input-operator-for-your-own-classes.md)  
  
## Vea también  
 [Programación con iostream](../standard-library/iostream-programming.md)