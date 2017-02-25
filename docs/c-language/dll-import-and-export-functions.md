---
title: "Funciones de importaci&#243;n y exportaci&#243;n de archivos DLL | Microsoft Docs"
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
  - "declarar funciones, con dllexport y dllimport"
  - "exportar DLL [C++]"
  - "dllexport (atributo) [C++], atributo de clase de almacenamiento"
  - "dllimport (atributo) [C++], atributo de clase de almacenamiento"
  - "DLL [C++], importar"
  - "atributos de clase de almacenamiento extendidos"
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Funciones de importaci&#243;n y exportaci&#243;n de archivos DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 La información más completa y actualizada sobre este tema se encuentra en [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
 Los modificadores de clase de almacenamiento **dllimport** y `dllexport` son extensiones específicas de Microsoft para el lenguaje C.  Estos modificadores definen explícitamente la interfaz de la DLL con su cliente \(el archivo ejecutable u otra DLL\).  Al declarar las funciones como `dllexport` deja de ser necesario el archivo de definición de módulo \(.DEF\).  También se pueden usar modificadores **dllimport** y `dllexport` con datos y objetos.  
  
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
  
## Vea también  
 [Definiciones de funciones de C](../c-language/c-function-definitions.md)