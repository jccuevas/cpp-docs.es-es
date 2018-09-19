---
title: Archivos DLL de extensión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afxdll
dev_langs:
- C++
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62bb287cca78875bf6c3ad11f426b23db3b6f7e1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718079"
---
# <a name="mfc-extension-dlls"></a>Archivos DLL de extensión MFC

Un archivo DLL de extensión de MFC es un archivo DLL que implementa clases reutilizables derivadas de las clases existentes de la biblioteca MFC (Microsoft Foundation Class).

Un archivo DLL de extensión de MFC incluye las siguientes características y requisitos:

- El archivo ejecutable cliente debe ser una aplicación MFC compilada con `_AFXDLL` definido.

- También puede usarse un archivo DLL de extensión MFC por una DLL de MFC normal que se vincule dinámicamente a MFC.

- DLL de extensión MFC debe compilarse con `_AFXEXT` definido. Esto fuerza `_AFXDLL` que también se defina y se asegura de que se extraigan las declaraciones apropiadas de los archivos de encabezado MFC. También garantiza que `AFX_EXT_CLASS` se define como `__declspec(dllexport)` al generar el archivo DLL, que es necesario si utiliza esta macro para declarar las clases en el archivo DLL de extensión MFC.

- DLL de extensión MFC no debe crear una instancia de una clase derivada de `CWinApp`, pero deben basarse en la aplicación cliente (o DLL) para proporcionar este objeto.

- Sin embargo, los archivos DLL de extensión MFC ofreciera un `DllMain` función y realice cualquier inicialización que sea necesaria.

Los archivos DLL de extensión se compilan con la versión de biblioteca de vínculos dinámicos de MFC (conocida también como la versión compartida de MFC). Solo los archivos ejecutables MFC (aplicaciones o archivos DLL de MFC estándar) que se generan con la versión compartida de MFC pueden usar un archivo DLL de extensión MFC. La aplicación cliente y el archivo DLL de extensión MFC deben usar la misma versión de MFCx0.dll. Con un archivo DLL de extensión MFC, puede derivar nuevas clases personalizadas de MFC y, a continuación, ofrecer esta versión extendida de MFC a las aplicaciones que llamen al archivo DLL.

También se puede utilizar archivos DLL de extensión para realizar transferencias de objetos derivados de MFC entre la aplicación y el archivo DLL. Las funciones miembro asociadas al objeto transferido existen en el módulo en que se creó el objeto. Dado que estas funciones se exportan correctamente al usar la versión compartida del archivo DLL de MFC, puede pasar libremente MFC o punteros a objetos derivados de MFC entre una aplicación y la carga de DLL de extensión MFC.

Un archivo DLL de extensión de MFC utiliza una versión compartida de MFC de la misma manera que una aplicación utiliza la versión compartida del archivo DLL de MFC, con unas consideraciones adicionales:

- No incluye un objeto derivado de `CWinApp`. Debe funcionar con el objeto derivado de `CWinApp` de la aplicación de cliente. Esto significa que la aplicación de cliente es propietaria del suministro principal de mensajes, el bucle de inactividad, etc.

- Llama a `AfxInitExtensionModule` en la función `DllMain`. Hay que comprobar el valor devuelto por esta función. Si `AfxInitExtensionModule` devuelve un valor cero, la función `DllMain` deberá devolver cero.

- Crea un **CDynLinkLibrary** objeto durante la inicialización si la extensión MFC DLL desea exportar `CRuntimeClass` objetos o recursos a la aplicación.

Antes de la versión 4.0 de MFC, este tipo de DLL se denominaba AFXDLL. AFXDLL hace referencia a la `_AFXDLL` símbolo de preprocesador que se define al compilar el archivo DLL.

Las bibliotecas de importación para la versión compartida de MFC se nombran según la convención descrita en [convenciones de nomenclatura para archivos DLL de MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Visual C++ proporciona versiones pregeneradas de los archivos DLL de MFC, junto con una serie de archivos DLL que no están basados en MFC y que puede utilizar y distribuir con las aplicaciones. Éstos aparecen documentados en Redist.txt, el cual se instala en la carpeta Archivos de programa\Microsoft Visual Studio.

Si va a utilizar un archivo .def para exportar, coloque el código siguiente al principio y al final del archivo de encabezado:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Estas cuatro líneas garantizan que el código se compilará correctamente para un archivo DLL de extensión MFC. Si se omiten estas cuatro líneas, el archivo DLL podría compilarse o vincularse incorrectamente.

Si necesita pasar un MFC o puntero de objeto derivado de MFC a o desde una DLL de MFC, el archivo DLL debe ser un archivo DLL de extensión MFC. Las funciones miembro asociadas al objeto transferido existen en el módulo en que se creó el objeto. Dado que estas funciones se exportan correctamente al usar la versión compartida del archivo DLL de MFC, puede pasar libremente MFC o punteros a objetos derivados de MFC entre una aplicación y la carga de DLL de extensión MFC.

Debido a problemas de exportación y eliminación de nombre de C++, la lista de exportación de una extensión de MFC DLL podría ser diferente entre las versiones de depuración y comerciales de la misma DLL y archivos DLL para distintas plataformas. La versión de lanzamiento del archivo MFCx0.dll tiene alrededor de 2.000 puntos de entrada exportados; la versión de depuración del archivo MFCx0D.dll tiene unos 3.000 puntos de entrada exportados.

## <a name="memory-management"></a>Administración de memoria

MFCx0.dll y todos los archivos DLL se carga en el espacio de direcciones de la aplicación cliente de extensión de MFC utilizan el mismo asignador de memoria, la carga de recursos y otros Estados globales de MFC como si estuvieran en la misma aplicación. Esto es importante porque las bibliotecas DLL que no son de MFC y los archivos DLL de MFC estándar realizan funciones exactamente opuestas y tienen cada sus archivos DLL asigna fuera de su propio bloque de memoria.

Si un archivo DLL de extensión MFC asigna memoria, esta memoria puede combinarse libremente con cualquier otro objeto asignado por la aplicación. Además, si no se puede ejecutar correctamente una aplicación que se vincula dinámicamente a MFC, la protección del sistema operativo mantendrá la integridad de cualquier otra aplicación MFC que comparta el archivo DLL.

De manera similar, otros estados globales de MFC, como el archivo ejecutable actual desde el que se cargan recursos, también se comparten entre la aplicación cliente y todos los archivos DLL de extensión de MFC, así como el propio MFCx0.dll.

## <a name="sharing-resources-and-classes"></a>Compartir recursos y clases

La exportación de recursos se realiza mediante una lista de recursos. Cada aplicación contiene una lista vinculada individualmente de **CDynLinkLibrary** objetos. Cuando se busca un recurso, la mayoría de las implementaciones MFC estándar que cargan recursos buscan primera en el módulo de recursos actual (`AfxGetResourceHandle`) y si no se encuentra el recurso recorren la lista de **CDynLinkLibrary** objetos al intentar cargar el recurso solicitado.

Recorrer la lista tiene la desventaja de que es un proceso un poco más lento y requiere administrar intervalos de identificadores de recursos. Tiene la ventaja de que una aplicación cliente que se vincula a varios archivos DLL de extensión MFC puede usar cualquier recurso proporcionado por el archivo DLL sin tener que especificar el identificador de instancia del archivo DLL. `AfxFindResourceHandle` es una API que se usa para recorrer la lista de recursos a fin de buscar una coincidencia determinada. Para ello, utiliza el nombre y el tipo de recurso, y devuelve el identificador de recurso donde se encontró por primera vez (o el valor NULL).

Si no desea recorrer la lista y sólo necesita cargar recursos desde una ubicación específica, utilice las funciones `AfxGetResourceHandle` y `AfxSetResourceHandle` para guardar el identificador antiguo y establecer el nuevo identificador. Asegúrese de restaurar el identificador de recurso antiguo antes de volver a la aplicación de cliente. Para obtener un ejemplo del uso de este enfoque para cargar un menú explícitamente, vea el archivo Testdll2 .cpp del ejemplo [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).

La creación dinámica de objetos MFC dado un nombre MFC es similar. El mecanismo de deserialización de objetos de MFC requiere que todos los objetos `CRuntimeClass` estén registrados para poder reconstruir creando dinámicamente objetos C++ del tipo requerido a partir de lo que estaba almacenado antes.

En el caso del ejemplo MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk), la lista de aspecto similar al siguiente:

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

MFCxx.dll suele estar al final de la lista de recursos y clases. MFCxx.dll incluye todos los recursos estándar de MFC, incluidas las cadenas de texto de los identificadores de comando estándar. Si lo coloca al final de la lista, los archivos DLL y la aplicación cliente no tendrán su propia copia de los recursos estándar de MFC, sino que se basarán en los recursos compartidos de MFCxx.dll.

Combinar los recursos y los nombres de clase de todos los archivos DLL en el espacio de nombres de la aplicación de cliente tiene la desventaja de que requiere ser cuidadoso al seleccionar identificadores o nombres.

El [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) ejemplo administra el espacio de nombres de recurso compartido mediante el uso de varios archivos de encabezado.

Si el archivo DLL de extensión MFC requiere mantener datos adicionales para cada aplicación, puede derivar una nueva clase de **CDynLinkLibrary** y crearla en `DllMain`. Cuando se ejecuta, el archivo DLL puede comprobar la lista actual de la aplicación de **CDynLinkLibrary** objetos que se va a buscar el correspondiente a ese archivo DLL de extensión MFC determinado.

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Inicializar un archivo DLL de extensión MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Sugerencias sobre el uso de archivos de recursos compartidos](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)