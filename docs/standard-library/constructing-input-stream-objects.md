---
title: "Construir objetos de flujo de entrada | Microsoft Docs"
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
  - "objetos de flujo de entrada"
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Construir objetos de flujo de entrada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si utiliza solo el objeto de `cin` , no necesita crear un flujo de entrada.  Debe crear un flujo de entrada si utiliza:  
  
-   [Constructores de la secuencia de archivo de entrada](#vclrfinputfilestreamconstructorsanchor8)  
  
-   [Constructores de la secuencia de la cadena de entrada](#vclrfinputstringstreamconstructorsanchor9)  
  
##  <a name="vclrfinputfilestreamconstructorsanchor8"></a> Constructores de la secuencia de archivo de entrada  
 Hay dos maneras de crear un archivo de entrada transmitir:  
  
-   Utilice el constructor de argumento de `void` , llame a la función miembro de `open` :  
  
    ```  
    ifstream myFile; // On the stack  
    myFile.open( "filename" );  
  
    ifstream* pmyFile = new ifstream; // On the heap  
    pmyFile->open( "filename" );  
    ```  
  
-   Especifique los indicadores de un nombre de archivo y el modo en la invocación de constructores, de esta manera abriendo el archivo durante la construcción:  
  
    ```  
    ifstream myFile( "filename" );  
    ```  
  
##  <a name="vclrfinputstringstreamconstructorsanchor9"></a> Constructores de la secuencia de la cadena de entrada  
 Los constructores de la secuencia de la cadena de entrada requieren la dirección de almacenamiento reservado, preinicializado:  
  
```  
string s("123.45");  
double amt;  
istringstream myString( s );   
//istringstream myString( "123.45" ) also works  
myString >> amt; // amt contains 123.45  
```  
  
## Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)