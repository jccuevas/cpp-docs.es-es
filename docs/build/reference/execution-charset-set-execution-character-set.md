---
title: -ejecución-juego de caracteres (juego de caracteres de ejecución de conjunto) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- execution-charset
- /execution-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7294270778d0b9351d3e58e8afd285f021bb0066
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="execution-charset-set-execution-character-set"></a>/Execution-CharSet (establecer el juego de caracteres en la ejecución)
Le permite especificar el juego para una aplicación ejecutable de caracteres de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/execution-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Argumentos  
 **IANA_name**  
 Juego de caracteres de definidos por la IANA.  
  
 **CPID**  
 El identificador de página de códigos.  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el **/execution-charset** opción para especificar un juego de caracteres de ejecución. El juego de caracteres de ejecución es la codificación utilizada para el texto del programa que se introduce en la fase de compilación después de que todos los pasos de preprocesamiento. Este juego de caracteres se utiliza para la representación interna de los literales de cadena o un carácter en el código compilado. Establezca esta opción para especificar el juego de caracteres extendido de ejecución debe usar cuando los archivos de origen incluyen caracteres que no se puede representables en el juego de caracteres de ejecución básica. Puede usar cualquier la IANA o juego de caracteres ISO o un punto (.) seguido por un identificador de página de código decimal de 3 a 5 dígitos para especificar el juego de caracteres a usar. Para obtener una lista de admite identificadores de página de código y los nombres del juego de caracteres, vea [identificadores de página de código](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de origen está en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de origen se codifica utilizando la página de códigos del usuario actual, a menos que haya especificado un juego de caracteres página nombre o el código mediante el uso de la **/source-charset** opción o **/utf-8** opción. Visual Studio permite guardar el código fuente de C++ mediante cualquiera de varias codificaciones de caracteres. Para obtener información acerca de los conjuntos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje.  
  
 Si desea establecer el juego de caracteres de origen y el juego de caracteres de ejecución a UTF-8, puede usar el **/utf-8** opción del compilador como un acceso directo. Es equivalente a especificar **/source-charset:utf-/execution 8-charset:utf-8** en la línea de comandos. Cualquiera de estas opciones también habilita la **/validate-charset** opción predeterminada.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración**, **C/C++**, **línea de comandos** carpeta.  
  
3.  En **opciones avanzadas**, agregue el **/execution-charset** opción y especifique la codificación preferida.  
  
4.  Elija **Aceptar** para guardar los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/Source-CharSet (conjunto de juego de caracteres de origen)](../../build/reference/source-charset-set-source-character-set.md)   
 [/UTF-8 (establecer origen y el ejecutable juegos de caracteres UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate/charset (Validar los caracteres compatibles)](../../build/reference/validate-charset-validate-for-compatible-characters.md)