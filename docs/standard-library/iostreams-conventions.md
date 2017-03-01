---
title: Convenciones de iostreams | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 247f9948c6f22e7d24c47966a398d1b33e054f45
ms.lasthandoff: 02/24/2017

---
# <a name="iostreams-conventions"></a>Convenciones de iostreams
Los encabezados de iostreams admiten las conversiones entre texto y formatos codificados, así como la entrada y la salida en archivos externos:  
  
|||  
|-|-|  
|[\<fstream>](../standard-library/fstream.md)|[\<iomanip>](../standard-library/iomanip.md)|  
|[\<ios>](../standard-library/ios.md)|[\<iosfwd>](../standard-library/iosfwd.md)|  
|[\<iostream>](../standard-library/iostream.md)|[\<istream>](../standard-library/istream.md)|  
|[\<ostream>](../standard-library/ostream.md)|[\<sstream>](../standard-library/sstream.md)|  
|[\<streambuf>](../standard-library/streambuf.md)|[\<strstream>](../standard-library/strstream.md)|  
  
 El uso más simple de iostreams solo requiere que incluya el encabezado [\<iostream>](../standard-library/iostream.md). Después, puede extraer valores de [cin](../standard-library/iostream.md#cin) o [wcin](../standard-library/iostream.md#wcin) para leer la entrada estándar. Las reglas para hacerlo se indican en la descripción de la clase [basic_istream](../standard-library/basic-istream-class.md). También puede insertar valores en [cout](../standard-library/iostream.md#cout) o [wcout](../standard-library/iostream.md#wcout) para escribir la salida estándar. Las reglas para hacerlo se indican en la descripción de la clase [basic_ostream](../standard-library/basic-ostream-class.md). El control de formato común para los extractores y los insertores se administra mediante la clase [basic_ios](../standard-library/basic-ios-class.md). La manipulación de esta información de formato mediante la extracción y la inserción de objetos es competencia de varios manipuladores.  
  
 Puede realizar las mismas operaciones de iostreams en los archivos que abra por su nombre, mediante las clases declaradas en [\<fstream>](../standard-library/fstream.md). Para convertir entre iostreams y objetos de clase [basic_string](../standard-library/basic-string-class.md), use las clases declaradas en [\<sstream>](../standard-library/sstream.md). Para hacer lo mismo con cadenas de C, use las clases declaradas en [\<strstream>](../standard-library/strstream.md).  
  
 Los encabezados restantes proporcionan servicios de soporte técnico, que normalmente solo interesan a los usuarios más avanzados de las clases iostreams.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


