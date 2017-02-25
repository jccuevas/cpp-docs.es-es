---
title: "Archivos DLL de extensi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afxdll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "biblioteca AFXDLL"
  - "DLL [C++], extensión"
  - "DLL de extensión [C++]"
  - "DLL de extensión [C++], acerca de los archivos DLL de extensión"
  - "memoria [C++], DLL"
  - "DLL de MFC [C++], archivos DLL de extensión"
  - "DLL de extensión MFC [C++]"
  - "compartir recursos [C++]"
  - "versiones de DLL compartidas [C++]"
  - "recursos compartidos [C++]"
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos DLL de extensi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un archivo DLL de extensión de MFC es un archivo DLL que implementa clases reutilizables derivadas de las clases existentes de la biblioteca MFC \(Microsoft Foundation Class\).  
  
 Un archivo DLL de extensión de MFC incluye las siguientes características y requisitos:  
  
-   El archivo ejecutable de cliente debe ser una aplicación MFC compilada con **\_AFXDLL** definido.  
  
-   También se puede utilizar un archivo DLL de extensión en un archivo DLL estándar vinculado dinámicamente a MFC.  
  
-   Los archivos DLL de extensión deben compilarse con `_AFXEXT` definido.  Esto fuerza a que también se defina **\_AFXDLL** y asegura que se extraigan las declaraciones apropiadas de los archivos de encabezado de MFC.  También asegura que se defina **AFX\_EXT\_CLASS** como **\_\_declspec\(dllexport\)** mientras se compila el archivo DLL, lo que será necesario si utiliza esta macro para declarar las clases en el archivo DLL de extensión.  
  
-   Los archivos DLL de extensión no deben crear una instancia de una clase derivada de `CWinApp`, pero deben basarse en la aplicación \(o el archivo DLL\) cliente para proporcionar este objeto.  
  
-   Sin embargo, los archivos DLL de extensión deben proporcionar una función `DllMain` y realizar cualquier tarea de inicialización que sea necesaria.  
  
 Los archivos DLL de extensión se compilan con la versión de biblioteca de vínculos dinámicos de MFC \(conocida también como la versión compartida de MFC\).  Sólo los archivos ejecutables de MFC \(aplicaciones o archivos DLL estándar\) integrados en la versión compartida de MFC pueden utilizar un archivo DLL de extensión.  La aplicación de cliente y el archivo DLL de extensión deben utilizar la misma versión de MFCx0.dll.  Mediante un archivo DLL de extensión, se pueden derivar nuevas clases personalizadas a partir de MFC y ofrecer esta versión extendida de MFC a las aplicaciones que llamen al archivo DLL.  
  
 También se puede utilizar archivos DLL de extensión para realizar transferencias de objetos derivados de MFC entre la aplicación y el archivo DLL.  Las funciones miembro asociadas al objeto transferido existen en el módulo en que se creó el objeto.  Dado que estas funciones se exportan correctamente al usar la versión compartida del archivo DLL de MFC, pueden pasarse punteros a objetos de MFC o derivados de MFC con libertad entre una aplicación y los archivos DLL de extensión que cargue.  
  
 Un archivo DLL de extensión de MFC utiliza una versión compartida de MFC de la misma manera que una aplicación utiliza la versión compartida del archivo DLL de MFC, con unas consideraciones adicionales:  
  
-   No incluye un objeto derivado de `CWinApp`.  Debe funcionar con el objeto derivado de `CWinApp` de la aplicación de cliente.  Esto significa que la aplicación de cliente es propietaria del suministro principal de mensajes, el bucle de inactividad, etc.  
  
-   Llama a `AfxInitExtensionModule` en la función `DllMain`.  Hay que comprobar el valor devuelto por esta función.  Si `AfxInitExtensionModule` devuelve un valor cero, la función `DllMain` deberá devolver cero.  
  
-   Crea un objeto **CDynLinkLibrary** durante la inicialización si el archivo DLL de extensión desea exportar objetos o recursos `CRuntimeClass` a la aplicación.  
  
 Antes de la versión 4.0 de MFC, este tipo de DLL se denominaba AFXDLL.  AFXDLL hace referencia al símbolo de preprocesador **\_AFXDLL** definido al compilar el archivo DLL.  
  
 Los nombres de las bibliotecas de importación para la versión compartida de MFC siguen la convención descrita en [Convenciones de nomenclatura para archivos DLL de MFC](../build/naming-conventions-for-mfc-dlls.md).  Visual C\+\+ proporciona versiones pregeneradas de los archivos DLL de MFC, junto con una serie de archivos DLL que no están basados en MFC y que puede utilizar y distribuir con las aplicaciones.  Éstos aparecen documentados en Redist.txt, el cual se instala en la carpeta Archivos de programa\\Microsoft Visual Studio.  
  
 Si va a utilizar un archivo .def para exportar, coloque el código siguiente al principio y al final del archivo de encabezado:  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 Estas cuatro líneas garantizan que el código se compilará correctamente para un archivo DLL de extensión.  Si se omiten estas cuatro líneas, el archivo DLL podría compilarse o vincularse incorrectamente.  
  
 Si necesita enviar a un archivo DLL de MFC \(o recibir del mismo\) un puntero a un objeto MFC o derivado de MFC, el archivo DLL deberá ser un archivo DLL de extensión.  Las funciones miembro asociadas al objeto transferido existen en el módulo en que se creó el objeto.  Dado que estas funciones se exportan correctamente al usar la versión compartida del archivo DLL de MFC, pueden pasarse punteros a objetos de MFC o derivados de MFC con libertad entre una aplicación y los archivos DLL de extensión que cargue.  
  
 A causa de la alteración de nombres de C\+\+ y los problemas de exportación, la lista de exportación de un archivo DLL de extensión puede ser distinta en las versiones de depuración y de lanzamiento del mismo archivo DLL y para archivos DLL de distintas plataformas.  La versión de lanzamiento del archivo MFCx0.dll tiene alrededor de 2.000 puntos de entrada exportados; la versión de depuración del archivo MFCx0D.dll tiene unos 3.000 puntos de entrada exportados.  
  
## Administración de la memoria  
 MFCx0.dll y todos los archivos DLL de extensión cargados en el espacio de direcciones de la aplicación cliente utilizarán el mismo asignador de memoria, la misma carga de recursos y otros estados globales de MFC como si estuvieran en la misma aplicación.  Esto es importante, ya que las bibliotecas DLL que no están basadas en MFC y los archivos DLL estándar realizan funciones exactamente opuestas y cada uno de sus archivos DLL asigna fuera de su propio bloque de memoria.  
  
 Si un archivo DLL de extensión asigna memoria, esta memoria puede combinarse libremente con cualquier otro objeto asignado por la aplicación.  Además, si no se puede ejecutar correctamente una aplicación que se vincula dinámicamente a MFC, la protección del sistema operativo mantendrá la integridad de cualquier otra aplicación MFC que comparta el archivo DLL.  
  
 De manera similar, otros estados globales de MFC, como el archivo ejecutable actual desde el que se cargan recursos, también se comparten entre la aplicación cliente y todos los archivos DLL de extensión de MFC, así como el propio MFCx0.dll.  
  
## Compartir recursos y clases  
 La exportación de recursos se realiza mediante una lista de recursos.  Cada aplicación contiene una lista vinculada y única de objetos **CDynLinkLibrary**.  Al buscar un recurso, la mayoría de las implementaciones MFC estándar que cargan recursos buscan primero en el módulo de recursos actual \(`AfxGetResourceHandle`\) y, si no se encuentra el recurso, recorren la lista de objetos **CDynLinkLibrary** para intentar cargar el recurso solicitado.  
  
 Recorrer la lista tiene la desventaja de que es un proceso un poco más lento y requiere administrar intervalos de identificadores de recursos.  Tiene la ventaja de que una aplicación cliente que se vincula a varios archivos DLL de extensión puede usar cualquier recurso proporcionado por un archivo DLL sin tener que especificar el identificador de instancia del archivo DLL.  `AfxFindResourceHandle` es una API que se usa para recorrer la lista de recursos a fin de buscar una coincidencia determinada.  Para ello, utiliza el nombre y el tipo de recurso, y devuelve el identificador de recurso donde se encontró por primera vez \(o el valor NULL\).  
  
 Si no desea recorrer la lista y sólo necesita cargar recursos desde una ubicación específica, utilice las funciones `AfxGetResourceHandle` y `AfxSetResourceHandle` para guardar el identificador antiguo y establecer el nuevo identificador.  Asegúrese de restaurar el identificador de recurso antiguo antes de volver a la aplicación de cliente.  Para ver un ejemplo de cómo utilizar este enfoque para cargar un menú explícitamente, vea el archivo Testdll2 .cpp del ejemplo [DLLHUSK](http://msdn.microsoft.com/es-es/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) de MFC.  
  
 La creación dinámica de objetos MFC dado un nombre MFC es similar.  El mecanismo de deserialización de objetos de MFC requiere que todos los objetos `CRuntimeClass` estén registrados para poder reconstruir creando dinámicamente objetos C\+\+ del tipo requerido a partir de lo que estaba almacenado antes.  
  
 En el caso del ejemplo [DLLHUSK](http://msdn.microsoft.com/es-es/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) de MFC, la lista tiene la siguiente apariencia:  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
               |                      |  
          TESTDLL2.DLL           TESTDLL2.DLL  
               |                      |  
          TESTDLL1.DLL           TESTDLL1.DLL  
               |                      |  
           MFCOxxD.DLL                |  
               |                      |  
           MFCDxxD.DLL                |  
               |                      |  
            MFCxxD.DLL            MFCxx.DLL  
```  
  
 donde *xx* es el número de versión; por ejemplo, 42 representa la versión 4.2.  
  
 MFCxx.dll suele estar al final de la lista de recursos y clases.  MFCxx.dll incluye todos los recursos estándar de MFC, incluidas las cadenas de texto de los identificadores de comando estándar.  Si lo coloca al final de la lista, los archivos DLL y la aplicación cliente no tendrán su propia copia de los recursos estándar de MFC, sino que se basarán en los recursos compartidos de MFCxx.dll.  
  
 Combinar los recursos y los nombres de clase de todos los archivos DLL en el espacio de nombres de la aplicación de cliente tiene la desventaja de que requiere ser cuidadoso al seleccionar identificadores o nombres.  
  
 El ejemplo [DLLHUSK](http://msdn.microsoft.com/es-es/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) administra el espacio de nombres del recurso compartido mediante varios archivos de encabezado.  
  
 Si el archivo DLL de extensión de MFC requiere mantener datos adicionales para cada aplicación, puede derivar una clase nueva a partir de **CDynLinkLibrary** y crearla en `DllMain`.  Cuando se ejecuta, el archivo DLL puede comprobar la lista de objetos **CDynLinkLibrary** de la aplicación actual para buscar el correspondiente a ese archivo DLL de extensión concreto.  
  
### ¿Qué desea hacer?  
  
-   [Inicializar un archivo DLL de extensión](../build/initializing-extension-dlls.md)  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Sugerencias para el uso de archivos de recursos compartidos](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
  
-   [Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)  
  
-   [Archivos DLL estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Utilizar archivos DLL de extensión de base de datos, OLE y Sockets en archivos DLL estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)