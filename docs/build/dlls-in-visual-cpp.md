---
title: Creación de archivos DLL de C/C++ en Visual Studio
description: Información general sobre por qué y cómo crear y usar archivos DLL con C++ en Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7083924f137fa9283da40404c7d15183e59c0b1c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422833"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Creación de archivos DLL de C/C++ en Visual Studio

En Windows, una biblioteca de vínculos dinámicos (DLL) es un tipo de archivo ejecutable que actúa como una biblioteca compartida de funciones y recursos. La vinculación dinámica es una funcionalidad del sistema operativo que permite a un archivo ejecutable llamar a funciones o usar recursos almacenados en un archivo independiente. Estas funciones y recursos se pueden compilar e implementar de forma independiente con respecto a los archivos ejecutables que los usan.

Un archivo DLL no es un archivo ejecutable independiente. Los archivos DLL se ejecutan en el contexto de las aplicaciones que los llaman. El sistema operativo carga el archivo DLL en el espacio de memoria de la aplicación. Este proceso se lleva a cabo cuando se carga la aplicación (*vinculación implícita*) o a petición en tiempo de ejecución (*vinculación explícita*). Los archivos DLL también hacen que sea más fácil compartir funciones y recursos en archivos ejecutables. Distintas aplicaciones pueden acceder al mismo tiempo al contenido de una única copia de un archivo DLL en la memoria.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Diferencias entre la vinculación dinámica y la vinculación estática

La vinculación estática copia todo el código objeto de una biblioteca estática en los archivos ejecutables que lo usan cuando se compilan. La vinculación dinámica solo incluye la información que Windows necesita en tiempo de ejecución para encontrar y cargar el archivo DLL que contiene una función o un elemento de datos. Cuando crea un archivo DLL, también crea una biblioteca de importación que contiene esta información. Cuando compila un archivo ejecutable que llama al archivo DLL, el enlazador usa los símbolos exportados en la biblioteca de importación para almacenar esta información para el cargador de Windows. Cuando el cargador carga un archivo DLL, este se asigna en el espacio de memoria de la aplicación. Si está presente, se llama a una función especial en el archivo DLL, `DllMain`, para que realice cualquier inicialización que requiera el archivo DLL.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Diferencias entre aplicaciones y archivos DLL

Aunque tanto los archivos DLL como las aplicaciones son módulos ejecutables, se diferencian en varios aspectos. La diferencia más obvia es que no se puede ejecutar un archivo DLL. Desde el punto de vista del sistema, hay dos diferencias fundamentales entre las aplicaciones y los archivos DLL:

- Una aplicación puede tener varias instancias ejecutándose simultáneamente en el sistema. En cambio, solo se puede tener una instancia de un archivo DLL.

- Una aplicación se puede cargar como un proceso. Puede ser propietaria de elementos como una pila, subprocesos de ejecución, una memoria global, identificadores de archivo y una cola de mensajes. Un archivo DLL no puede poseer estos elementos.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Ventajas de usar archivos DLL

La vinculación dinámica a código y recursos ofrece varias ventajas con respecto a la vinculación estática:

- La vinculación dinámica ahorra memoria y reduce el intercambio. Muchos procesos pueden usar simultáneamente un archivo DLL, al compartir una sola copia de los elementos de solo lectura del archivo DLL en la memoria. En cambio, todas las aplicaciones compiladas mediante una biblioteca vinculada estáticamente tienen una copia completa del código de la biblioteca que Windows debe cargar en la memoria.

- La vinculación dinámica ahorra espacio en disco y ancho de banda. Varias aplicaciones pueden compartir una única copia del archivo DLL en disco. En cambio, las aplicaciones compiladas con una biblioteca de vínculos estáticos tienen el código de biblioteca vinculado en la imagen ejecutable. Esto usa más espacio en disco y ocupa más ancho de banda al transferirse.

- El mantenimiento, las revisiones de seguridad y las actualizaciones pueden ser más fáciles. Cuando las aplicaciones usan funciones comunes en un archivo DLL, se pueden implementar correcciones de errores e actualizaciones en el archivo DLL. Cuando se actualizan los archivos DLL, no es necesario volver a compilar a vincular las aplicaciones que los emplean. Pueden usar el nuevo archivo DLL en cuanto se implementa. Por el contrario, cuando se realizan correcciones en código objeto vinculado estáticamente, es necesario volver a vincular y a implementar cada aplicación que lo use.

- Puede usar archivos DLL para ofrecer soporte técnico posventa. Por ejemplo, se puede modificar un archivo DLL de un controlador de vídeo de forma que permita una presentación que no estaba disponible en la versión comercial.

- Puede usar la vinculación explícita para detectar y cargar archivos DLL en tiempo de ejecución. Por ejemplo, las extensiones de aplicación que agregan nuevas funcionalidades a la aplicación sin volver a compilarla o a implementarla.

- La vinculación dinámica facilita la compatibilidad con aplicaciones escritas en lenguajes de programación diferentes. Programas creados con distintos lenguajes de programación pueden llamar a la misma función DLL siempre que sigan la convención de llamada a la función. Los programas y la función DLL deben ser compatibles en los siguientes aspectos: el orden en el que la función espera que los argumentos se inserten en la pila; el hecho de que sea la función o la aplicación la responsable de limpiar la pila; y el hecho de que los argumentos se pasen en registros.

- La vinculación dinámica proporciona un mecanismo para ampliar las clases de la biblioteca MFC (Microsoft Foundation Class). Puede derivar clases a partir de las clases MFC existentes y colocarlas en un archivo DLL de extensión de MFC para que las utilicen las aplicaciones MFC.

- La vinculación dinámica facilita la creación de versiones internacionales de la aplicación. Los archivos DLL son una manera práctica de proporcionar recursos específicos de la configuración regional, lo que facilita enormemente la creación de versiones internacionales de una aplicación. En lugar de enviar muchas versiones localizadas de la aplicación, puede colocar las cadenas y las imágenes de cada idioma en un archivo DLL de recursos independiente. Después, la aplicación puede cargar los recursos adecuados para esa configuración regional en tiempo de ejecución.

Una posible desventaja del uso de archivos DLL es que la aplicación no es autónoma. Depende de la existencia de un módulo DLL independiente, que debe implementar o comprobar usted mismo como parte de la instalación.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Más información sobre la creación y el uso de archivos DLL

En los artículos siguientes se proporciona información detallada sobre cómo crear archivos DLL de C/C++ en Visual Studio.

[Tutorial: Creación y uso de una biblioteca de vínculos dinámicos (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
Describe cómo crear y usar una DLL con Visual Studio.

[Tipos de archivos DLL](kinds-of-dlls.md)\
Proporciona información sobre las distintas clases de archivos DLL que se pueden compilar.

[Preguntas más frecuentes sobre archivos DLL](dll-frequently-asked-questions.md)\
Proporciona respuestas a las preguntas más frecuentes sobre los archivos DLL.

[Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md)\
Describe el vínculo a un archivo DLL explícito e implícito.

[Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)\
Describe el código de inicialización del archivo DLL que se debe ejecutar cuando este se carga.

[Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++](run-time-library-behavior.md)\
Describe la secuencia de inicio del archivo DLL de la biblioteca en tiempo de ejecución.

[LoadLibrary y AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)\
Describe el uso de `LoadLibrary` y `AfxLoadLibrary` para vincular explícitamente a un archivo DLL en tiempo de ejecución.

[GetProcAddress](getprocaddress.md)\
Explica el uso de `GetProcAddress` para obtener la dirección de una función exportada en el archivo DLL.

[FreeLibrary y AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)\
Describe el uso de `FreeLibrary` y `AfxFreeLibrary` cuando el módulo del archivo DLL ya no se necesita.

[Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)\
Describe la ruta de acceso de búsqueda que usa el sistema operativo Windows para encontrar un archivo DLL en el sistema.

[Estados de módulos de un archivo DLL de MFC estándar vinculado dinámicamente a MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)\
Describe los estados de módulos de un archivo DLL de MFC estándar vinculado dinámicamente a MFC.

[Archivos DLL de extensión MFC](extension-dlls-overview.md)\
Describe los archivos DLL que suelen implementar clases reutilizables derivadas de las clases existentes de MFC.

[Crear un archivo DLL de recursos](creating-a-resource-only-dll.md)\
Describe un archivo DLL sólo de recursos, que únicamente contiene recursos, como iconos, mapas de bits, cadenas y cuadros de diálogo.

[Recursos localizados en aplicaciones MFC: archivos DLL satélite](localized-resources-in-mfc-applications-satellite-dlls.md)\
Proporciona compatibilidad mejorada con archivos DLL satélite, una característica que le ayuda a crear aplicaciones en múltiples idiomas.

[Importar y exportar](importing-and-exporting.md)\
Describe símbolos públicos de importación a una aplicación o funciones de exportación de un archivo DLL.

[Tecnología activa y archivos DLL](active-technology-and-dlls.md)\
Permite a los servidores de objetos implementarse dentro de un archivo DLL.

[Automation en un archivo DLL](automation-in-a-dll.md)\
Describe qué proporciona la opción Automation en el Asistente para archivos DLL de MFC.

[Convenciones de nomenclatura para archivos DLL de MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
Explica cómo los archivos DLL y las bibliotecas incluidos en MFC utilizan una convención de nomenclatura estructurada.

[Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](calling-dll-functions-from-visual-basic-applications.md)\
Describe cómo llamar a funciones DLL desde aplicaciones de Visual Basic.

## <a name="related-sections"></a>Secciones relacionadas

[Uso de MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)\
Describe los archivos DLL de MFC estándar, que permiten usar la biblioteca MFC como parte de una biblioteca de vínculos dinámicos de Windows.

[Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)\
Describe la forma de usar las bibliotecas de vínculos dinámicos compartidas MFCxx.dll y MFCxxD.dll (donde x es el número de versión de MFC) con aplicaciones MFC y archivos DLL de extensión de MFC.
