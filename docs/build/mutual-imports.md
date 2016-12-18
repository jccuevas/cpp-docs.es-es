---
title: "Importaciones mutuas | Microsoft Docs"
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
  - "símbolo de preprocesador _AFXEXT"
  - "AFX_DATA"
  - "AFX_EXT_CLASS (macro)"
  - "importaciones circulares"
  - "DLL [C++], importar"
  - "archivos ejecutables [C++], importar"
  - "exportar DLL [C++], importaciones mutuas"
  - "DLL de extensión [C++], importaciones mutuas"
  - "importar archivos DLL [C++], importaciones mutuas"
  - "DLL con importaciones mutuas [C++]"
  - "importar mutuamente archivos ejecutables [C++]"
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Importaciones mutuas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La exportación a otro archivo ejecutable \(o la importación desde otro archivo ejecutable\) presenta complicaciones cuando las importaciones son mutuas \(o circulares\).  Por ejemplo, dos archivos DLL importan símbolos entre sí, de forma similar a las funciones mutuamente recursivas.  
  
 El problema de importar mutuamente archivos ejecutables \(generalmente archivos DLL\) es que ninguno se pueden compilar sin compilar al otro primero.  Cada proceso de compilación requiere, como entrada, una biblioteca de importación producida por el otro proceso de compilación.  
  
 La solución es utilizar la herramienta LIB con la opción \/DEF, que produce una biblioteca de importación sin compilar el archivo ejecutable.  Con esta herramienta, puede compilar todas las bibliotecas de importación que necesite, independientemente de cuántos archivos DLL haya implicados y de la complejidad de las dependencias.  
  
 La solución general para procesar importaciones mutuas es la siguiente:  
  
1.  Utilice un archivo DLL cada vez. Cualquier orden es válido, aunque algunos órdenes son mejores. Si todas las bibliotecas de importación necesarias existen y están actualizadas, ejecute LINK para compilar el archivo ejecutable \(DLL\).  Esto produce una biblioteca de importación.  En caso contrario, ejecute LIB para producir una biblioteca de importación.  
  
     Si ejecuta LIB con la opción \/DEF se producirá un archivo adicional con la extensión .EXP.  Este archivo .EXP deberá utilizarse posteriormente para compilar el archivo ejecutable.  
  
2.  Después de utilizar LINK o LIB para compilar todas las bibliotecas de importación, vuelva para ejecutar LINK a fin de compilar los archivos ejecutables que no se compilaron en el paso anterior.  Tenga en cuenta que el archivo .exp correspondiente debe especificarse en la línea de comandos de LINK.  
  
     Si ejecutó antes la herramienta LIB para producir una biblioteca de importación para DLL1, LIB también habrá producido el archivo DLL1.exp.  Debe utilizar DLL1.exp como entrada de LINK al compilar DLL1.dll.  
  
 La ilustración siguiente muestra una solución para dos archivos DLL con importaciones mutuas, DLL1 y DLL2.  El primer paso es ejecutar LIB en DLL1, con la opción \/DEF establecida.  Este primer paso produce DLL1.lib, una biblioteca de importación, y DLL1.exp.  En el segundo paso, la biblioteca de importación se utiliza para compilar DLL2, que a su vez produce una biblioteca de importación para los símbolos de DLL2.  En el tercer paso se compila DLL1, con DLL1.exp y DLL2.lib como entrada.  Tenga en cuenta que no es necesario un archivo .exp para DLL2, puesto que no se utilizó LIB para compilar la biblioteca de importación de DLL2.  
  
 ![Uso de importaciones mutuas para vincular dos archivos DLL](../build/media/vc37yj1.png "vc37YJ1")  
Vincular dos archivos DLL con importaciones mutuas  
  
## Limitaciones de \_AFXEXT  
 Puede utilizar el símbolo de preprocesador `_AFXEXT` para los archivos DLL de extensión siempre que no tenga varios niveles de archivos DLL de extensión.  Si tiene archivos DLL de extensión que puede llamar o derivar desde clases de sus propios archivos DLL de extensión, que se derivan de las clases MFC, debe utilizar su propio símbolo de preprocesador para evitar la ambigüedad.  
  
 El problema es que en Win32, debe declarar explícitamente todos los datos como **\_\_declspec\(dllexport\)** si se van a exportar desde un archivo DLL, y como **\_\_declspec\(dllimport\)** si se van a importar desde un archivo DLL.  Cuando defina `_AFXEXT`, los encabezados de MFC garantizarán que **AFX\_EXT\_CLASS** esté correctamente definido.  
  
 Cuando tenga varios niveles, un símbolo como **AFX\_EXT\_CLASS** no será suficiente, puesto que un archivo DLL de extensión puede exportar clases nuevas, así como importar otras clases desde otro archivo DLL de extensión.  Para solucionar este problema, utilice un símbolo especial de preprocesador que indique que está compilando el archivo DLL, no utilizándolo.  Por ejemplo, imagine dos archivos DLL de extensión, A.dll y B.dll.  Cada uno de ellos exporta algunas clases en A.h y B.h, respectivamente.  B.dll usa las clases de A.dll.  Los archivos de encabezado presentarían el siguiente aspecto:  
  
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
  
 A.dll se compila con `/D A_IMPL` y B.dll se compila con `/D B_IMPL`.  Si se usan símbolos independientes para cada archivo DLL, `CExampleB` se exporta y `CExampleA` se importa al compilar B.dll.  `CExampleA` se exporta al compilar A.dll y se importa cuando la usa B.dll \(o algún otro cliente\).  
  
 Este tipo de organización en niveles no se puede hacer sin utilizar los símbolos de preprocesador integrados **AFX\_EXT\_CLASS** y `_AFXEXT`.  La técnica antes descrita soluciona este problema de la misma manera que el mecanismo que utiliza MFC al compilar sus archivos DLL de extensión de tecnologías activas, bases de datos y redes.  
  
## No se exporta la clase completa  
 Cuando no se exporte la clase completa, deberá asegurarse de que los elementos de datos necesarios creados por las macros MFC se exportan correctamente.  Esto puede realizarse volviendo a definir `AFX_DATA` para la macro específica de la clase.  Debe hacerse siempre que no se exporte toda la clase.  
  
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
  
### ¿Qué desea hacer?  
  
-   [Exportar de un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Exportar desde un archivo DLL mediante archivos .DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX\_EXT\_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C\+\+ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Determinar el método de exportación que se va a utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante \_\_declspec\(dllimport\)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### ¿Sobre qué desea obtener más información?  
  
-   [La utilidad LIB y la opción \/DEF](../build/reference/lib-reference.md)  
  
## Vea también  
 [Importar y exportar](../build/importing-and-exporting.md)