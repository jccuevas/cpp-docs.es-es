---
title: "Funciones de importación y exportación de archivos DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 78d1dacd764a7d171c9cacb54a64fab241f8603a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="dll-import-and-export-functions"></a>Funciones de importación y exportación de archivos DLL
**Específicos de Microsoft**  
  
 La información más completa y actualizada sobre este tema se encuentra en [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
 Los modificadores de clase de almacenamiento **dllimport** y `dllexport` son extensiones específicas de Microsoft para el lenguaje C. Estos modificadores definen explícitamente la interfaz de la DLL con su cliente (el archivo ejecutable u otra DLL). Al declarar las funciones como `dllexport` deja de ser necesario el archivo de definición de módulo (.DEF). También se pueden usar los modificadores **dllimport** y `dllexport` con datos y objetos.  
  
 Los modificadores de clase de almacenamiento **dllimport** y `dllexport` deben usarse con la palabra clave de sintaxis de atributo extendido, `__declspec`, como se muestra en este ejemplo:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllExport int j;  
DllExport int n;  
```  
  
 Para obtener información específica sobre la sintaxis de los modificadores extendidos de clase de almacenamiento, vea [Atributos extendidos de clase de almacenamiento](../c-language/c-extended-storage-class-attributes.md).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Definiciones de función de C](../c-language/c-function-definitions.md)