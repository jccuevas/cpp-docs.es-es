---
title: "Archivos DLL en Visual C++ | Microsoft Docs"
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
  - "DLL [C++]"
  - "DLL [C++], acerca de las DLL"
  - "vinculación dinámica [C++]"
  - "archivos ejecutables [C++]"
  - "vincular [C++], dinámica y estática"
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos DLL en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una biblioteca de vínculos dinámicos \(DLL\) es un archivo ejecutable que actúa como una biblioteca compartida de funciones y recursos.  La vinculación dinámica permite a un archivo ejecutable llamar a funciones o usar recursos almacenados en un archivo independiente.  Estas funciones y recursos se pueden compilar e implementar de forma independiente con respecto a los archivos ejecutables que los usan.  El sistema operativo puede cargar el archivo DLL en el espacio de memoria del archivo ejecutable cuando este se cargue o a petición en tiempo de ejecución.  Los archivos DLL también hacen que sea más fácil compartir funciones y recursos en archivos ejecutables.  Distintas aplicaciones pueden acceder al mismo tiempo al contenido de una única copia de un archivo DLL en la memoria.  
  
 La vinculación estática copia todo el código de objeto de un archivo .lib en un archivo ejecutable.  La vinculación dinámica solo incluye la información necesaria en tiempo de ejecución para encontrar y cargar el archivo DLL que contiene una función o un elemento de datos.  Cuando crea un archivo DLL, también crea un archivo .lib que contiene esta información.  Cuando compila un archivo ejecutable que llama al archivo DLL, el vinculador usa los símbolos exportados en el archivo .lib para almacenar esta información para el cargador.  Cuando el cargador carga un archivo DLL, el archivo DLL se asigna en el espacio de memoria de su archivo ejecutable.  Se llama a una función especial en el archivo DLL, `DllMain`, para que realice cualquier inicialización que requiera el archivo DLL.  
  
 El uso de la vinculación dinámica, en lugar de la vinculación estática, ofrece varias ventajas.  Al usar archivos DLL, puede ahorrar espacio de memoria y reducir el intercambio.  Si varias aplicaciones pueden usar una única copia de un archivo DLL, puede ahorrar espacio en disco y ancho de banda de descarga.  Los archivos DLL se pueden implementar y actualizar por separado, lo que le permite proporcionar actualizaciones de software y soporte técnico post\-venta sin tener que volver a compilar y enviar todo el código.  Los archivos DLL son una manera cómoda de proporcionar recursos específicos de una configuración regional, lo que puede proporcionar compatibilidad con programas multilenguaje y facilitar la creación de versiones internacionales de sus aplicaciones.  
  
 En los siguientes temas se proporciona información detallada sobre cómo programar archivos DLL.  
  
## En esta sección  
 [Tutorial: Crear y utilizar una biblioteca de vínculos dinámicos \(C\+\+\)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
 Describe cómo crear y usar una DLL con Visual Studio.  
  
 [Diferencias entre aplicaciones y archivos DLL](../build/differences-between-applications-and-dlls.md)  
 Describe las principales diferencias entre las aplicaciones y los archivos DLL.  
  
 [Ventajas de utilizar archivos DLL](../build/advantages-of-using-dlls.md)  
 Describe las ventajas del vínculo dinámico.  
  
 [Tipos de archivos DLL](../build/kinds-of-dlls.md)  
 Proporciona información sobre las distintas clases de archivos DLL que se pueden compilar.  
  
 [Preguntas más frecuentes sobre archivos DLL](../build/dll-frequently-asked-questions.md)  
 Proporciona respuestas a las preguntas más frecuentes sobre los archivos DLL.  
  
 [Vincular un ejecutable a un archivo DLL](../build/linking-an-executable-to-a-dll.md)  
 Describe el vínculo a un archivo DLL explícito e implícito.  
  
 [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
 Describe el código de inicialización que incluye el archivo DLL \(de asignación de memoria, por ejemplo\) que deberá ejecutarse cuando se cargue el archivo DLL.  
  
 [Comportamiento de la biblioteca en tiempo de ejecución](../build/run-time-library-behavior.md)  
 Describe cómo la biblioteca en tiempo de ejecución realiza la secuencia de inicio del archivo DLL.  
  
 [LoadLibrary y AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
 Describe el uso de **LoadLibrary** y `AfxLoadLibrary` para vincularse explícitamente a un archivo DLL en tiempo de ejecución.  
  
 [GetProcAddress](../build/getprocaddress.md)  
 Explica la utilización de **GetProcAddress** para obtener la dirección de una función exportada en el archivo DLL.  
  
 [FreeLibrary y AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
 Describe la utilización de **FreeLibrary** y `AfxFreeLibrary` cuando el módulo del archivo DLL ya no se necesita.  
  
 [Ruta de búsqueda de Windows para encontrar un archivo DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
 Describe la ruta de acceso de búsqueda que usa el sistema operativo Windows para encontrar un archivo DLL en el sistema.  
  
 [Estados de módulos de un archivo DLL estándar vinculado dinámicamente a MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
 Describe los estados de módulos de un archivo DLL vinculado dinámicamente a MFC.  
  
 [Archivos DLL de extensión](../build/extension-dlls-overview.md)  
 Muestra un archivo DLL que implementa clases reutilizables derivadas de las clases existentes de la biblioteca MFC \(Microsoft Foundation Classes\).  
  
 [Crear un archivo DLL de recursos](../build/creating-a-resource-only-dll.md)  
 Describe un archivo DLL sólo de recursos, que únicamente contiene recursos, como iconos, mapas de bits, cadenas y cuadros de diálogo.  
  
 [Recursos localizados en aplicaciones MFC: archivos DLL satélite](../build/localized-resources-in-mfc-applications-satellite-dlls.md)  
 Proporciona compatibilidad mejorada con archivos DLL satélite, una característica que le ayuda a crear aplicaciones en múltiples idiomas.  
  
 [Importar y exportar](../build/importing-and-exporting.md)  
 Describe símbolos públicos de importación a una aplicación o funciones de exportación de un archivo DLL.  
  
 [Tecnología activa y archivos DLL](../build/active-technology-and-dlls.md)  
 Permite a los servidores de objetos implementarse dentro de un archivo DLL.  
  
 [Automatización en un archivo DLL](../build/automation-in-a-dll.md)  
 Describe qué proporciona la opción Automatización en el Asistente para archivos DLL de MFC.  
  
 [Convenciones de nomenclatura para archivos DLL de MFC](../build/naming-conventions-for-mfc-dlls.md)  
 Explica cómo los archivos DLL y las bibliotecas incluidos en MFC utilizan una convención de nomenclatura estructurada.  
  
 [Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)  
 Describe cómo llamar a funciones DLL desde aplicaciones de Visual Basic.  
  
## Secciones relacionadas  
 [Utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
 Describe los archivos DLL normales, que le permiten usar la biblioteca MFC como parte de una biblioteca de vínculos dinámicos de Windows.  
  
 [Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)  
 Describe la forma de utilizar las bibliotecas de vínculos dinámicos compartidas MFCxx.dll y MFCxxD.dll \(donde x es el número de versión de MFC\) con aplicaciones MFC y archivos DLL de extensión.  
  
 [\(NOTINBUILD\)Visual C\+\+ Programming Methodologies](http://msdn.microsoft.com/es-es/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 Proporciona vínculos a temas que proporcionan información conceptual sobre las bibliotecas de Visual C\+\+ y temas que tratan diversas tecnologías y técnicas de codificación.