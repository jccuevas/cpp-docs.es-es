---
title: Importar a una aplicación mediante __declspec (dllimport) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- __declspec
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82974ec688fbe688c98188c2e99a54462da81165
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368840"
---
# <a name="importing-into-an-application-using-declspecdllimport"></a>Importar a una aplicación mediante __declspec(dllimport)
Se dice que un programa que utiliza símbolos públicos definidos por un archivo DLL importa dichos símbolos. Al crear archivos de encabezado para las aplicaciones que usan los archivos DLL para generar, utilice **__declspec (dllimport)** en las declaraciones de los símbolos públicos. La palabra clave **__declspec (dllimport)** funciona tanto si exporta con archivos .def o con la **__declspec (dllexport)** (palabra clave).  
  
 Para que el código sea más legible, defina una macro para **__declspec (dllimport)** y, a continuación, utilice la macro para declarar cada símbolo importado:  
  
```  
#define DllImport   __declspec( dllimport )  
  
DllImport int  j;  
DllImport void func();  
```  
  
 Usar **__declspec (dllimport)** es opcional en declaraciones de función, pero el compilador produce un código más eficaz si utiliza esta palabra clave. Sin embargo, debe usar **__declspec (dllimport)** para el ejecutable importador pueda tener acceso a los símbolos de datos públicos y objetos de los archivos DLL. Tenga en cuenta que los usuarios del archivo DLL aún deben vincularse a una biblioteca de importación.  
  
 Puede utilizar el mismo archivo de encabezado para el archivo DLL y para la aplicación de cliente. Para ello, utilice un símbolo de preprocesador especial que indique si está compilando el archivo DLL o la aplicación de cliente. Por ejemplo:  
  
```  
#ifdef _EXPORTING  
   #define CLASS_DECLSPEC    __declspec(dllexport)  
#else  
   #define CLASS_DECLSPEC    __declspec(dllimport)  
#endif  
  
class CLASS_DECLSPEC CExampleA : public CObject  
{ ... class definition ... };  
```  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Vea también  
 [Importación a una aplicación](../build/importing-into-an-application.md)