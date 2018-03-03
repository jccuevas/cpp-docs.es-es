---
title: Importaciones mutuas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bfd31cd4e5776555137daf002c076e14d4031f89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mutual-imports"></a>Importaciones mutuas
Exportar o importar a otro archivo ejecutable presenta complicaciones cuando las importaciones mutuas (o circulares). Por ejemplo, dos archivos DLL importan símbolos entre sí, similar a funciones mutuamente recursivas.  
  
 El problema de importar mutuamente archivos ejecutables (generalmente archivos DLL) es que no se pueden generar sin generar al otro primero. Cada proceso de compilación requiere, como entrada, una biblioteca de importación generada por el otro proceso de compilación.  
  
 La solución consiste en utilizar la herramienta LIB con la opción/DEF, que produce una biblioteca de importación sin compilar el archivo ejecutable. Con esta herramienta, puede generar todas las bibliotecas de importación que necesita, independientemente de cuántos archivos DLL haya implicados y la complejidad de las dependencias.  
  
 La solución general para procesar importaciones mutuas es:  
  
1.  Llevar a su vez cada DLL. (Cualquier orden es factible, aunque algunos pedidos resultan más óptimos). Si todas las bibliotecas de importación necesarias existen y están actualizadas, ejecute LINK para generar el archivo ejecutable (DLL). Esto produce una biblioteca de importación. En caso contrario, ejecute LIB para generar una biblioteca de importación.  
  
     Ejecutar LIB con la opción/DEF genera un archivo adicional con un. Extensión EXP. El archivo. Archivo EXP debe usarse posteriormente para generar el archivo ejecutable.  
  
2.  Después de utilizar LINK o LIB para generar todas las bibliotecas de importación, vuelva atrás y ejecute LINK para generar los archivos ejecutables que no se compilaron en el paso anterior. Tenga en cuenta que el archivo .exp correspondiente debe especificarse en la línea de vínculo.  
  
     Si hubiera ejecutado la herramienta LIB para producir una biblioteca de importación para DLL1, LIB también habrá producido el archivo DLL1.exp así. Debe utilizar DLL1.exp como entrada de LINK al generar DLL1.dll.  
  
 En la siguiente ilustración muestra una solución para dos archivos DLL que importan, DLL1 y DLL2. Paso 1 consiste en ejecutar LIB, con la opción/DEF establecida, en DLL1. Paso 1 produce DLL1.lib, una biblioteca de importación y DLL1.exp. En el paso 2, la biblioteca de importación se utiliza para generar DLL2, que a su vez produce una biblioteca de importación para los símbolos de DLL2. Paso 3 genera DLL1, con DLL1.exp y DLL2.lib como entrada. Tenga en cuenta que no es necesario un archivo .exp para DLL2 porque no se utilizó LIB para generar la biblioteca de importación de DLL2.  
  
 ![Uso de importaciones mutuas para vincular dos archivos DLL](../build/media/vc37yj1.gif "vc37YJ1")  
Vincular dos archivos DLL con importaciones mutuas  
  
## <a name="limitations-of-afxext"></a>Limitaciones de _AFXEXT  
 Puede usar el `_AFXEXT` símbolo de preprocesador para la extensión MFC DLL siempre y cuando no tiene varios niveles de archivos DLL de extensión MFC. Si tiene archivos DLL que llamar o derivar desde clases de sus propios archivos DLL, que se derivan de las clases MFC, de extensión MFC de extensión de MFC debe utilizar su propio símbolo de preprocesador para evitar la ambigüedad.  
  
 El problema es que en Win32, debe declarar explícitamente los datos como **__declspec (dllexport)** si no se puede exportar desde un archivo DLL, y **__declspec (dllimport)** si se va a importar desde un archivo DLL. Cuando se define `_AFXEXT`, los encabezados de MFC Asegúrese de que **AFX_EXT_CLASS** se definió correctamente.  
  
 Si tiene varios niveles, un símbolo como **AFX_EXT_CLASS** no es suficiente, porque un archivo DLL de extensión MFC puede exportar clases nuevas, así como importar otras clases desde otro archivo DLL de extensión MFC. Para solucionar este problema, utilice un símbolo de preprocesador especial que indique que está generando el archivo DLL, frente al uso de la DLL. Por ejemplo, imagine dos archivos DLL de extensión MFC,.dll y B.dll. Cada uno de ellos exporta algunas clases en A.h y B.h, respectivamente. B.dll utiliza las clases de.dll. Los archivos de encabezado sería algo parecido a esto:  
  
```  
/* A.H */  
#ifdef A_IMPL  
   #define CLASS_DECL_A   __declspec(dllexport)  
#else  
   #define CLASS_DECL_A   __declspec(dllimport)  
#endif  
  
class CLASS_DECL_A CExampleA : public CObject  
{ ... class definition ... };  
  
// B.H  
#ifdef B_IMPL  
   #define CLASS_DECL_B   __declspec(dllexport)  
#else  
   #define CLASS_DECL_B   __declspec(dllimport)  
#endif  
  
class CLASS_DECL_B CExampleB : public CExampleA  
{ ... class definition ... };  
...  
```  
  
 .Dll se genera con `/D A_IMPL` y B.dll se genera con `/D B_IMPL`. Si utiliza símbolos independientes para cada DLL `CExampleB` se exporta y `CExampleA` se importa al generar B.dll. `CExampleA`se exporta al generar A.dll y se importa al ser utilizada por B.dll (o algún otro cliente).  
  
 No se puede realizar este tipo de distribución en capas cuando se usa la integrada **AFX_EXT_CLASS** y `_AFXEXT` símbolos de preprocesador. La técnica descrita anteriormente soluciona este problema de forma no al contrario que el mecanismo de MFC utiliza al generar sus tecnologías activas, base de datos y archivos DLL de extensión de MFC de la red.  
  
## <a name="not-exporting-the-entire-class"></a>No exporte toda la clase  
 Cuando no se exporta una clase completa, tendrá que asegurarse de que los elementos de datos necesarios creados por las macros MFC se exportan correctamente. Esto puede hacerse mediante la redefinición de `AFX_DATA` macro su específica de la clase. Esto debe hacerse siempre que no se exporte toda la clase.  
  
 Por ejemplo:  
  
```  
/* A.H */  
#ifdef A_IMPL  
   #define CLASS_DECL_A  _declspec(dllexport)  
#else  
   #define CLASS_DECL_A  _declspec(dllimport)  
#endif  
  
#undef  AFX_DATA  
#define AFX_DATA CLASS_DECL_A  
  
class CExampleA : public CObject  
{  
   DECLARE_DYNAMIC()  
   CLASS_DECL_A int SomeFunction();  
   //... class definition ...  
};  
  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Exportar desde un archivo DLL mediante archivos. DEF (archivos)](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [La utilidad LIB y la opción/DEF](../build/reference/lib-reference.md)  
  
## <a name="see-also"></a>Vea también  
 [Importar y exportar](../build/importing-and-exporting.md)