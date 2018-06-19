---
title: Opciones del compilador y del vinculador (C++ / CX) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e43418555722090c325c85bd4e77204640791b32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088485"
---
# <a name="compiler-and-linker-options-ccx"></a>Opciones del compilador y del vinculador (C++/CX)
Una variable de entorno, C++ / CX compilador opciones y las opciones del vinculador admiten la compilación de aplicaciones para el tiempo de ejecución de Windows.  
  
## <a name="library-path"></a>Ruta de acceso a la biblioteca  
 La variable de entorno %LIBPATH% especifica la ruta de acceso predeterminada para los archivos .winmd.  
  
## <a name="compiler-options"></a>Opciones del compilador  
  
|Opción|Descripción|  
|------------|-----------------|  
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /ZW:nostdlib|Habilita las extensiones de lenguaje de Windows en tiempo de ejecución.<br /><br /> El parámetro `nostdlib` impide que el compilador use la ruta de acceso de búsqueda estándar predefinida para buscar archivos .winmd y de ensamblado.<br /><br /> La opción del compilador **/ZW** especifica de manera implícita las siguientes opciones del compilador:<br /><br /> -   **/Fi** vccorlib.h, que fuerza la inclusión del archivo de encabezado vccorlib.h que define muchos tipos que son requeridos por el compilador.<br />-   [/FU](../build/reference/fu-name-forced-hash-using-file.md) Windows.winmd, que fuerza la inclusión del archivo de metadatos Windows.winmd proporcionado por el sistema operativo e define muchos tipos en el tiempo de ejecución de Windows.<br />-   **/FU** Platform.winmd, que fuerza la inclusión del archivo de metadatos Platform.winmd ofrecido por el compilador y que define la mayoría de los tipos de la familia de Platform de espacios de nombres.|  
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|Agrega un directorio, que se especifica mediante el parámetro *dir* , a la ruta de acceso de búsqueda que usa el compilador para buscar archivos .winmd y de ensamblado.|  
|**/FU**  *archivo*|Fuerza la inclusión del módulo especificado o el archivo .winmd. Es decir, no tienes que especificar `#using` *archivo* en el código fuente. El compilador fuerza automáticamente la inclusión de su propio archivo de metadatos de Windows, Platform.winmd.|  
|/D "WINAPI_FAMILY=2"|Crea una definición que permite el uso de un subconjunto del SDK de Win32 que es compatible con el tiempo de ejecución de Windows.|  
  
## <a name="linker-options"></a>Opciones del enlazador  
  
|Opción|Descripción|  
|------------|-----------------|  
|/APPCONTAINER[:NO]|Marca el archivo ejecutable como que se puede ejecutar en appcontainer (solo).|  
|/ WINMD [: {N&AMP;#124;SÓLO}]|Emite un archivo .winmd y un archivo binario asociado. Esta opción se debe pasar al enlazador para que se emita un .winmd.<br /><br /> **NO:** no genera un archivo .winmd, pero sí un archivo binario.<br /><br /> **ONLY:** genera un archivo .winmd, pero no un archivo binario.|  
|/WINMDFILE:*nombre_de_archivo*|El nombre del archivo .winmd que se va a generar, en lugar del nombre de archivo .winmd predeterminado. Si se especifican varios nombres de archivo en la línea de comandos, se usará el último nombre.|  
|/WINMDDELAYSIGN[:NO]|Firma parcialmente el archivo .winmd y coloca la clave pública en el archivo binario.<br /><br /> **NO:**(predeterminado) no firma el archivo .winmd.<br /><br /> /WINMDDELAYSIGN no tiene ningún efecto a menos que también se especifiquen /WINMDKEYFILE o /WINMDKEYCONTAINER.|  
|/WINMDKEYCONTAINER:*nombre*|Especifica un contenedor de claves para firmar un ensamblado. El parámetro *nombre* corresponde al contenedor de claves que se usa para firmar el archivo de metadatos.|  
|/WINMDKEYFILE:*nombre_de_archivo*|Especifica una clave o un par de claves para firmar el ensamblado. El parámetro *filename* corresponde a la clave que se usa para firmar el archivo de metadatos.|  
  
### <a name="remarks"></a>Comentarios  
 Al usar **/ZW**, el compilador se vincula automáticamente a la versión de DLL de runtime de C (CRT). No se permite la vinculación a la versión de biblioteca estática y cualquier uso de funciones de CRT que no se permiten en una aplicación de la plataforma Universal de Windows provocará un error de tiempo de compilación.  
  
## <a name="see-also"></a>Vea también  
 [Compilar aplicaciones y bibliotecas](../cppcx/building-apps-and-libraries-c-cx.md)