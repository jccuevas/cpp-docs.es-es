---
title: Construir objetos de flujo de salida | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: ca8d4e9a44f4550d02e6d224ce0130d15e81da14
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="constructing-output-stream-objects"></a>Construir objetos de flujo de salida
Si solo usa los objeto predefinidos `cout`, `cerr` o `clog`, no es necesario que cree un flujo de salida. Debe usar constructores para:  
  
- [Constructores de flujo de archivos de salida](#vclrfoutputfilestreamconstructorsanchor1)  
  
- [Constructores de flujo de cadenas de salida](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1"></a> Constructores de flujo de archivos de salida  
 Puede crear un flujo de archivo de salida de una de estas dos maneras:  
  
-   Use el constructor predeterminado y después llame a la función miembro `open`.  
  
 ```  
    ofstream myFile; // Static or on the stack  
    myFile.open("filename");

 
    ofstream* pmyFile = new ofstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   Especifique un nombre de archivo y marcas de modo en la llamada al constructor.  
  
 ```  
    ofstream myFile("filename", ios_base::out);
```  
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2"></a> Constructores de flujo de cadenas de salida  
 Para crear un flujo de cadenas de salida, puede usar `ostringstream` de la siguiente manera:  
  
```  
    using namespace std;  
string sp;  
ostringstream myString;  
myString <<"this is a test" <<ends;  
sp = myString.str();
// Obtain string  
cout <<sp <endl;   
```  
  
 El "manipulador" `ends` agrega el carácter nulo de terminación necesario a la cadena.  
  
## <a name="see-also"></a>Vea también  
 [Flujos de salida](../standard-library/output-streams.md)


