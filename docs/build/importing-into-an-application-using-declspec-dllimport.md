---
title: "Importar a una aplicaci&#243;n mediante __declspec(dllimport) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__declspec"
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) (palabra clave) [C++]"
  - "importar archivos DLL [C++], __declspec(dllimport)"
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Importar a una aplicaci&#243;n mediante __declspec(dllimport)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se dice que un programa que utiliza símbolos públicos definidos por un archivo DLL importa dichos símbolos.  Cuando cree archivos de encabezado para aplicaciones que utilizan los archivos DLL para generar, utilice **\_\_declspec\(dllimport\)** en las declaraciones de los símbolos públicos.  La palabra clave **\_\_declspec\(dllimport\)** funciona tanto si exporta con archivos .def como con la palabra clave **\_\_declspec\(dllexport\)**.  
  
 Para hacer que el código sea más legible, defina una macro para **\_\_declspec\(dllimport\)** y después utilice la macro para declarar cada símbolo importado:  
  
```  
#define DllImport   __declspec( dllimport )  
  
DllImport int  j;  
DllImport void func();  
```  
  
 El uso de **\_\_declspec\(dllimport\)** es opcional en declaraciones de función, pero el compilador produce un código más eficaz si utiliza esta palabra clave.  Sin embargo, debe utilizar **\_\_declspec\(dllimport\)** para que el ejecutable importador pueda tener acceso a los símbolos y objetos de datos públicos del archivo DLL.  Tenga en cuenta que los usuarios del archivo DLL aún deben vincularse a una biblioteca de importación.  
  
 Puede utilizar el mismo archivo de encabezado para el archivo DLL y para la aplicación de cliente.  Para ello, utilice un símbolo de preprocesador especial que indique si está compilando el archivo DLL o la aplicación de cliente.  Por ejemplo:  
  
```  
#ifdef _EXPORTING  
   #define CLASS_DECLSPEC    __declspec(dllexport)  
#else  
   #define CLASS_DECLSPEC    __declspec(dllimport)  
#endif  
  
class CLASS_DECLSPEC CExampleA : public CObject  
{ ... class definition ... };  
```  
  
## ¿Qué desea hacer?  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## Vea también  
 [Importar a una aplicación](../build/importing-into-an-application.md)