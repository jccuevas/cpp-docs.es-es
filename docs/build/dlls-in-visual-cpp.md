---
title: Crear C/C++ dll en Visual Studio
ms.date: 07/18/2019
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 33f002143e306c99b4d17b7a01ddd4a9738e38e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493276"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Crear C/C++ dll en Visual Studio

En Windows, una biblioteca de vínculos dinámicos (DLL) es un tipo de archivo ejecutable que actúa como una biblioteca compartida de funciones y recursos. La vinculación dinámica es una funcionalidad del sistema operativo que permite a un ejecutable llamar a funciones o usar recursos almacenados en un archivo independiente. Estas funciones y recursos se pueden compilar e implementar de forma independiente con respecto a los archivos ejecutables que los usan. Un archivo DLL no es un archivo ejecutable independiente; se ejecuta en el contexto de una aplicación que lo llama. El sistema operativo puede cargar el archivo DLL en el espacio de memoria de una aplicación cuando la aplicación se carga (*vinculación implícita*) o a petición en tiempo de ejecución (*vinculación explícita*). Los archivos DLL también hacen que sea más fácil compartir funciones y recursos en archivos ejecutables. Distintas aplicaciones pueden acceder al mismo tiempo al contenido de una única copia de un archivo DLL en la memoria.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Diferencias entre la vinculación dinámica y la vinculación estática

La vinculación estática copia todo el código objeto de una biblioteca estática en los ejecutables que lo usan cuando se compilan. La vinculación dinámica solo incluye la información que necesita Windows en tiempo de ejecución para buscar y cargar el archivo DLL que contiene un elemento de datos o una función. Al crear un archivo DLL, también se crea una biblioteca de importación que contiene esta información. Al compilar un archivo ejecutable que llama al archivo DLL, el vinculador utiliza los símbolos exportados en la biblioteca de importación para almacenar esta información para el cargador de Windows. Cuando el cargador carga un archivo DLL, el archivo DLL se asigna al espacio de memoria de la aplicación. Si está presente, se llama a una función especial `DllMain`en el archivo dll,, para realizar cualquier inicialización que requiera el archivo dll.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Diferencias entre aplicaciones y archivos dll

Aunque los archivos dll y las aplicaciones son módulos ejecutables, difieren de varias maneras. Para el usuario final, la diferencia más obvia es que los archivos dll no son aplicaciones que se pueden ejecutar directamente. Desde el punto de vista del sistema, hay dos diferencias fundamentales entre las aplicaciones y los archivos DLL:

- Una aplicación puede tener varias instancias ejecutándose simultáneamente en el sistema, mientras que sólo se puede ejecutar una instancia de un archivo DLL.

- Una aplicación se puede cargar como un proceso que puede poseer elementos como una pila, subprocesos de ejecución, memoria global, identificadores de archivo y una cola de mensajes, pero no una DLL.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Ventajas del uso de archivos dll

La vinculación dinámica a código y recursos ofrece varias ventajas con respecto a la vinculación estática:

- La vinculación dinámica ahorra memoria y reduce el intercambio. Muchos procesos pueden utilizar un archivo DLL simultáneamente, compartiendo una única copia de los elementos de solo lectura de un archivo DLL en la memoria. En cambio, cada aplicación que se compila mediante una biblioteca vinculada estáticamente tiene una copia completa del código de la biblioteca que Windows debe cargar en la memoria.

- La vinculación dinámica ahorra espacio en disco y ancho de banda. Varias aplicaciones pueden compartir una única copia del archivo DLL en disco. Por el contrario, cada aplicación compilada con una biblioteca de vínculos estáticos tiene el código de biblioteca vinculado en su imagen ejecutable, que usa más espacio en disco y toma más ancho de banda para transferir.

- El mantenimiento, las correcciones de seguridad y las actualizaciones pueden ser más fáciles. Cuando las aplicaciones usan funciones comunes en un archivo DLL, siempre y cuando no cambien los argumentos de función y los valores devueltos, puede implementar correcciones de errores e implementar actualizaciones en el archivo DLL. Cuando se actualizan los archivos dll, no es necesario volver a compilar ni volver a crear el vínculo de las aplicaciones que los usan, y se usa la nueva DLL tan pronto como se implementa. En cambio, las correcciones que se realizan en el código de objeto vinculado estáticamente requieren volver a vincular y volver a implementar todas las aplicaciones que la usan.

- Puede usar archivos DLL para ofrecer soporte técnico comercial. Por ejemplo, se puede modificar un archivo DLL de un controlador de vídeo de forma que permita una presentación que no estaba disponible en la versión comercial.

- Puede usar la vinculación explícita para detectar y cargar archivos dll en tiempo de ejecución, como extensiones de aplicación que agregan una nueva funcionalidad a la aplicación sin volver a generarlo o volver a implementarlo.

- La vinculación dinámica facilita la compatibilidad con aplicaciones escritas en lenguajes de programación diferentes. Programas creados con distintos lenguajes de programación pueden llamar a la misma función DLL siempre que sigan la convención de llamada a la función. Los programas y la función DLL deben coincidir en los siguientes aspectos: el orden de inserción de los argumentos de la función en la pila, si la función o la aplicación es responsable de limpiar la pila y si se pasan argumentos en registros.

- La vinculación dinámica proporciona un mecanismo para ampliar las clases de la biblioteca MFC. Puede derivar clases a partir de las clases MFC existentes y colocarlas en un archivo DLL de extensión de MFC para que las utilicen las aplicaciones MFC.

- La vinculación dinámica facilita la creación de versiones internacionales de la aplicación. Los archivos dll son una forma cómoda de proporcionar recursos específicos de la configuración regional, lo que facilita enormemente la creación de versiones internacionales de una aplicación. En lugar de enviar muchas versiones localizadas de la aplicación, puede colocar las cadenas e imágenes para cada idioma en un archivo DLL de recursos independiente y, a continuación, la aplicación puede cargar los recursos adecuados para esa configuración regional en tiempo de ejecución.

Una posible desventaja del uso de archivos dll es que la aplicación no es independiente; depende de la existencia de un módulo DLL independiente que debe implementarse o comprobarse como parte de la instalación.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Más información sobre cómo crear y usar archivos dll

En los temas siguientes se proporciona información detallada sobre cómo crear CC++ /dll en Visual Studio.

[Tutorial: Creación y uso de una biblioteca de vínculos dinámicos (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
Describe cómo crear y usar una DLL con Visual Studio.

[Tipos de archivos DLL](kinds-of-dlls.md)<br/>
Proporciona información sobre las distintas clases de archivos DLL que se pueden compilar.

[Preguntas más frecuentes sobre DLL](dll-frequently-asked-questions.md)<br/>
Proporciona respuestas a las preguntas más frecuentes sobre los archivos DLL.

[Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md)<br/>
Describe el vínculo a un archivo DLL explícito e implícito.

[Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)<br/>
Describe el código de inicialización del archivo DLL que se debe ejecutar cuando se carga el archivo DLL.

[Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++](run-time-library-behavior.md)<br/>
Describe cómo la biblioteca en tiempo de ejecución realiza la secuencia de inicio del archivo DLL.

[LoadLibrary y AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)<br/>
Describe el uso de LoadLibrary `AfxLoadLibrary` y para vincularse explícitamente a un archivo dll en tiempo de ejecución.

[GetProcAddress](getprocaddress.md)<br/>
Describe el uso de **GetProcAddress** para obtener la dirección de una función exportada en el archivo dll.

[FreeLibrary y AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)<br/>
Describe el uso de FreeLibrary `AfxFreeLibrary` y cuando el módulo DLL ya no se necesita.

[Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)<br/>
Describe la ruta de acceso de búsqueda que usa el sistema operativo Windows para encontrar un archivo DLL en el sistema.

[Estados de módulos de un archivo DLL de MFC estándar vinculado dinámicamente a MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)<br/>
Describe los Estados de módulos de un archivo DLL de MFC normal vinculado dinámicamente a MFC.

[Archivos DLL de extensión MFC](extension-dlls-overview.md)<br/>
Muestra un archivo DLL que implementa clases reutilizables derivadas de las clases existentes de la biblioteca MFC (Microsoft Foundation Classes).

[Creación de un archivo DLL de recursos](creating-a-resource-only-dll.md)<br/>
Describe un archivo DLL sólo de recursos, que únicamente contiene recursos, como iconos, mapas de bits, cadenas y cuadros de diálogo.

[Recursos localizados en aplicaciones MFC: archivos DLL satélite](localized-resources-in-mfc-applications-satellite-dlls.md)<br/>
Proporciona compatibilidad mejorada con archivos DLL satélite, una característica que le ayuda a crear aplicaciones en múltiples idiomas.

[Importar y exportar](importing-and-exporting.md)<br/>
Describe símbolos públicos de importación a una aplicación o funciones de exportación de un archivo DLL.

[Tecnología activa y archivos DLL](active-technology-and-dlls.md)<br/>
Permite a los servidores de objetos implementarse dentro de un archivo DLL.

[Automatización en un archivo DLL](automation-in-a-dll.md)<br/>
Describe qué proporciona la opción Automation en el Asistente para archivos DLL de MFC.

[Convenciones de nomenclatura para archivos DLL de MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)<br/>
Explica cómo los archivos DLL y las bibliotecas incluidos en MFC utilizan una convención de nomenclatura estructurada.

[Llamar a funciones DLL desde aplicaciones Visual Basic](calling-dll-functions-from-visual-basic-applications.md)<br/>
Describe cómo llamar a funciones DLL desde aplicaciones de Visual Basic.

## <a name="related-sections"></a>Secciones relacionadas

[Usar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)<br/>
Describe los archivos dll de MFC normales, que permiten utilizar la biblioteca MFC como parte de una biblioteca de vínculos dinámicos de Windows.

[Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)<br/>
Describe cómo puede usar las bibliotecas de vínculos dinámicos compartidas MFCxx. dll y MFCxxD. dll (donde x es el número de versión de MFC) con aplicaciones MFC y archivos dll de extensión de MFC.
