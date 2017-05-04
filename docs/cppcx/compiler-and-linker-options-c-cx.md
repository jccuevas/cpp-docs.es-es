---
title: "Opciones del compilador y del vinculador (C++-CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 10
---
# Opciones del compilador y del vinculador (C++-CX)
Una variable de entorno, las opciones del compilador [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] y las opciones del enlazador admiten la compilación de aplicaciones para [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
## Ruta de acceso a la biblioteca  
 La variable de entorno %LIBPATH% especifica la ruta de acceso predeterminada para los archivos .winmd.  
  
## Opciones del compilador  
  
|Opción|Descripción|  
|------------|-----------------|  
|[\/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> \/ZW:nostdlib|Habilita las extensiones de lenguaje [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].<br /><br /> El parámetro `nostdlib` impide que el compilador use la ruta de acceso de búsqueda estándar predefinida para buscar archivos .winmd y de ensamblado.<br /><br /> La opción del compilador [\/ZW](../build/reference/zw-windows-runtime-compilation.md) especifica de manera implícita las siguientes opciones del compilador:<br /><br /> -   [\/FI](../build/reference/fi-name-forced-include-file.md) vccorlib.h, que fuerza la inclusión del archivo de encabezado vccorlib.h que define muchos de los tipos requeridos por el compilador.<br />-   [\/FU](~/build/reference/fu-name-forced-hash-using-file.md) Windows.winmd, que fuerza la inclusión del archivo de metadatos Windows.winmd ofrecidos por el sistema operativo y que define muchos tipos en [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].<br />-   [\/FU](~/build/reference/fu-name-forced-hash-using-file.md) Platform.winmd, que fuerza la inclusión del archivo de metadatos Platform.winmd ofrecido por el compilador y que define la mayoría de los tipos de la familia de Platform de espacios de nombres.|  
|[\/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|Agrega un directorio, que se especifica mediante el parámetro *dir*, a la ruta de acceso de búsqueda que usa el compilador para buscar archivos .winmd y de ensamblado.|  
|[\/FU](~/build/reference/fu-name-forced-hash-using-file.md) *archivo*|Fuerza la inclusión del módulo especificado o el archivo .winmd. Es decir, no hay que especificar `#using`*archivo* en el código fuente. El compilador fuerza automáticamente la inclusión de su propio archivo de metadatos de Windows, Platform.winmd.|  
|\/D "WINAPI\_FAMILY\=2"|Crea una definición que permite el uso de un subconjunto del SDK de Win32 que es compatible con [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].|  
  
## Opciones del enlazador  
  
|Opción|Descripción|  
|------------|-----------------|  
|\/APPCONTAINER\[:NO\]|Marca el archivo ejecutable como que se puede ejecutar en appcontainer \(solo\).|  
|\/WINMD\[:{NO&#124;ONLY}\]|Emite un archivo .winmd y un archivo binario asociado. Esta opción se debe pasar al enlazador para que se emita un .winmd.<br /><br /> **NO:** no genera un archivo .winmd, pero sí un archivo binario.<br /><br /> **ONLY:** genera un archivo .winmd, pero no un archivo binario.|  
|\/WINMDFILE:*nombre\_de\_archivo*|El nombre del archivo .winmd que se va a generar, en lugar del nombre de archivo .winmd predeterminado. Si se especifican varios nombres de archivo en la línea de comandos, se usará el último nombre.|  
|\/WINMDDELAYSIGN\[:NO\]|Firma parcialmente el archivo .winmd y coloca la clave pública en el archivo binario.<br /><br /> **NO:** \(predeterminado\) no firma el archivo .winmd.<br /><br /> \/WINMDDELAYSIGN no tiene ningún efecto a menos que también se especifiquen \/WINMDKEYFILE o \/WINMDKEYCONTAINER.|  
|\/WINMDKEYCONTAINER:*nombre*|Especifica un contenedor de claves para firmar un ensamblado. El parámetro *nombre* corresponde al contenedor de claves que se usa para firmar el archivo de metadatos.|  
|\/WINMDKEYFILE:*nombre\_de\_archivo*|Especifica una clave o un par de claves para firmar el ensamblado. El parámetro *filename* corresponde a la clave que se usa para firmar el archivo de metadatos.|  
  
## Comentarios  
 Al usar **\/ZW**, el compilador se vincula automáticamente a la versión de DLL de runtime de C \(CRT\). No se permite la vinculación a la versión de la biblioteca estática y cualquier uso de las funciones de CRT que no esté permitido en una aplicación [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] provocará un error en tiempo de compilación.  
  
## Vea también  
 [Compilar aplicaciones y bibliotecas](../cppcx/building-apps-and-libraries-c-cx.md)