---
title: Flujos de entrada/salida | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: efb67656ef5d864a5acec2dce304a8ea8fd011c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="inputoutput-streams"></a>Flujos de entrada/salida
`basic_iostream`, que se define en el archivo de encabezado \<istream>, es la plantilla de clase para los objetos que administran flujos de E/S basados en caracteres de entrada y de salida.  
  
 Hay dos definiciones de tipo que definen las especializaciones específicas de caracteres de `basic_iostream` y que pueden facilitar la lectura del código: `iostream` (que no se debe confundirse con el archivo de encabezado \<iostream>) es un flujo de E/S basado en `basic_iostream<char>` y `wiostream` es un flujo de E/S basado en `basic_iostream<wchar_t>`.  
  
 Para obtener más información, vea [Clase basic_iostream](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md) y [wiostream](../standard-library/basic-iostream-class.md).  
  
 De `basic_iostream` deriva la plantilla de clase `basic_fstream`, que se usa para transmitir datos de caracteres a y desde archivos.  
  
 También hay definiciones de tipos que proporcionan especializaciones específicas de caracteres de `basic_fstream`. Se trata de `fstream`, que es un flujo de E/S de archivos basado en `char`, y `wfstream`, que es un flujo de E/S de archivos que se basa en `wchar_t`. Para obtener más información, vea [Clase basic_fstream](../standard-library/basic-fstream-class.md), [fstream](../standard-library/basic-fstream-class.md) y [wfstream](../standard-library/basic-fstream-class.md). El uso de estas definiciones de tipos requiere la inclusión del archivo de encabezado \<fstream>.  
  
> [!NOTE]
>  Cuando se usa un objeto `basic_fstream` para realizar operaciones de E/S de archivos, aunque el búfer subyacente contenga posiciones designadas de forma independiente para la lectura y la escritura, las posiciones de la entrada actual y de la salida actual están vinculadas y, por lo tanto, la lectura de algunos datos mueve la posición de salida.  
  
 La plantilla de clase `basic_stringstream` y su especialización común, `stringstream`, se usan a menudo para trabajar con objetos de flujo de E/S para insertar y extraer datos de caracteres. Para obtener más información, vea [Clase basic_stringstream](../standard-library/basic-stringstream-class.md).  
  
## <a name="see-also"></a>Vea también  
 [stringstream](../standard-library/basic-stringstream-class.md)   
 [Clase basic_stringstream](../standard-library/basic-stringstream-class.md)   
 [\<sstream>](../standard-library/sstream.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)



