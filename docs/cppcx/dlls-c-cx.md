---
title: "DLL (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: 21
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 21
---
# DLL (C++/CX)
Puedes usar Visual Studio para crear un archivo DLL para Win32 estándar o un archivo DLL para el componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] que se pueden utilizar en las aplicaciones [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]. Un archivo DLL estándar creado con una versión de Visual Studio o el compilador de Visual C\+\+ anterior a [!INCLUDE[vs_dev11_long](../cppcx/includes/vs-dev11-long-md.md)] puede no cargarse correctamente en una aplicación [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] y no superar la prueba de comprobación de la aplicación en la [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)].  
  
## Archivos DLL de componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]  
 En casi todos casos, cuando desees crear un archivo DLL para usarlo en una aplicación de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], créalo como un componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] mediante la plantilla de proyecto de ese nombre. Puedes crear un proyecto de componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] para archivos DLL que tengan tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] públicos o privados. Se puede tener acceso a un componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] desde aplicaciones escritas en cualquier lenguaje compatible con [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. De forma predeterminada, las opciones de configuración del compilador para un proyecto de componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] utilizan el modificador **\/ZW**. Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre de la DLL no tiene que coincidir con el nombre del archivo .winmd.  
  
 Para obtener más información, consulta [Crear componentes de Windows en tiempo de ejecución en C\+\+](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf).  
  
#### Para hacer referencia a un binario componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] de terceros en tu proyecto  
  
1.  Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes**, elige el botón **Agregar nueva referencia**.  
  
2.  Un componente de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] consta de un archivo DLL y un archivo .winmd que contiene los metadatos. Normalmente, estos archivos se encuentran en la misma carpeta. En el panel izquierdo del cuadro de diálogo **Agregar referencia**, elige el botón **Examinar** y después navega hasta la ubicación del archivo DLL y su archivo .winmd. Para más información, vea [Tutorial: crear y usar los SDK de extensiones](http://msdn.microsoft.com/es-es/001e2fca-3d56-43ab-a5e0-0561d085679f).  
  
## Archivos DLL estándar  
 Puedes crear un archivo DLL estándar para código de C\+\+ que no utilice ni produzca tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] públicos sino de una aplicación de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]. Usa el tipo de proyecto DLL de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] cuando solo desees migrar una DLL existente para compilarla en esta versión de Visual Studio pero no quieres convertir el código en un proyecto de componente de Windows en tiempo de ejecución. Al utilizar los pasos siguientes, la DLL se implementará en paralelo con el ejecutable de la aplicación en el paquete .appx.  
  
#### Para crear un archivo DLL estándar en Visual Studio  
  
1.  En la barra de menús, elige **Archivo**, **Nuevo**, **Proyecto** y, a continuación, selecciona la plantilla DLL de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)].  
  
2.  Escribe un nombre para el proyecto y, a continuación, haz clic en el botón **Aceptar**.  
  
3.  Agrega el código. Asegúrate de utilizar `__declspec(dllexport)` para las funciones que deseas exportar, por ejemplo, `__declspec(dllexport) Add(int I, in j);`.  
  
4.  Agrega `#include winapifamily.h` para incluir el archivo de encabezado de Windows SDK para las aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] y establece la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.  
  
#### Para hacer referencia a un proyecto DLL estándar de la misma solución  
  
1.  Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades comunes**, elige el botón **Agregar nueva referencia**.  
  
2.  En el panel izquierdo, selecciona **Solución** y, a continuación, activa la casilla adecuada en el panel derecho.  
  
3.  En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.  
  
#### Para hacer referencia a un binario DLL estándar  
  
1.  Copia el archivo DLL, el archivo .lib y el archivo de encabezado y pégalos en una ubicación conocida, por ejemplo, en la carpeta del proyecto actual.  
  
2.  Abre el menú contextual del proyecto que utilizará el archivo DLL y, a continuación, elige **Propiedades**. En la página **Propiedades de configuración**, **Vinculador**, **Entrada**, agrega el archivo .lib como una dependencia.  
  
3.  En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.  
  
#### Para migrar un archivo DLL para Win32 existente para la compatibilidad de aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]  
  
1.  Crea un proyecto de tipo DLL de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] y agrégale el código fuente existente.  
  
2.  Agrega `#include winapifamily.h` para incluir el archivo de encabezado de Windows SDK para las aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] y establece la macro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.  
  
3.  En los archivos de código fuente, agrega una instrucción `#include` para el archivo de encabezado de DLL, según sea necesario.  
  
## Vea también  
 [\(NOTINBUILD\) Temas avanzados](http://msdn.microsoft.com/es-es/1ccff0cf-a6cc-47ef-a05f-eba6307b3ced)