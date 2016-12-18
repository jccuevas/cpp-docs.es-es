---
title: "Construir objetos de flujo de salida | Microsoft Docs"
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
  - "objetos de flujo de salida"
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Construir objetos de flujo de salida
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si utiliza sólo `cout`predefinido, `cerr`, o los objetos de `clog` , no necesita construir una secuencia de salida.  Debe usar los constructores para:  
  
-   [Constructores de la secuencia de archivo de salida](#vclrfoutputfilestreamconstructorsanchor1)  
  
-   [Constructores de la secuencia de la cadena de salida](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1"></a> Constructores de la secuencia de archivo de salida  
 Puede crear un archivo de salida transmitir de dos maneras:  
  
-   Utilice el constructor predeterminado, y llame a la función miembro de `open` .  
  
    ```  
    ofstream myFile; // Static or on the stack  
    myFile.open( "filename" );  
  
    ofstream* pmyFile = new ofstream; // On the heap  
    pmyFile->open( "filename" );  
    ```  
  
-   Especifique los indicadores de un nombre de archivo y el modo en la llamada al constructor.  
  
    ```  
    ofstream myFile( "filename", ios_base::out);  
    ```  
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2"></a> Constructores de la secuencia de la cadena de salida  
 Para construir una secuencia de la cadena de salida, puede utilizar `ostringstream` así:  
  
```  
   using namespace std;  
string sp;  
ostringstream myString;  
myString << "this is a test" << ends;  
sp = myString.str();  // Obtain string  
cout << sp < endl;   
```  
  
 `ends` “manipulador” agrega el carácter null de terminación necesario a string.  
  
## Vea también  
 [Flujos de salida](../standard-library/output-streams.md)