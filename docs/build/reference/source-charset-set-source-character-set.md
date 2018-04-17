---
title: -origen-juego de caracteres (juego de caracteres de origen del conjunto) | Documentos de Microsoft
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
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba414318f9954df331dd05d0f3e2cc2b85c8ad11
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="source-charset-set-source-character-set"></a>/Source-CharSet (conjunto de juego de caracteres de origen)
Le permite especificar el juego para una aplicación ejecutable de caracteres de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/source-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Argumentos  
 **IANA_name**  
 Juego de caracteres de definidos por la IANA.  
  
 **CPID**  
 El identificador de página de código como un número decimal.  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el **/source-charset** opción permite especificar un carácter extendido origen desea para usar cuando los archivos de origen incluyen caracteres que no están representados en el juego de caracteres de origen básico. El juego de caracteres de origen es la codificación utilizada para interpretar el texto de origen del programa en la representación interna utilizada como entrada para las fases de preprocesamiento antes de la compilación. La representación interna, a continuación, se convierte en el juego de caracteres de ejecución para almacenar valores de cadena y carácter en el archivo ejecutable. Puede usar cualquier la IANA o juego de caracteres ISO o un punto (.) seguido por un identificador de página de código decimal de 3 a 5 dígitos para especificar el juego de caracteres a usar. Para obtener una lista de admite identificadores de página de código y los nombres del juego de caracteres, vea [identificadores de página de código](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de origen está en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de origen se codifica utilizando la página de códigos del usuario actual, a menos que especifique un juego de caracteres página nombre o el código mediante el uso de la **/source-charset** opción. Visual Studio permite guardar el código fuente de C++ mediante cualquiera de varias codificaciones de caracteres. Para obtener más información acerca de los conjuntos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje.  
  
 El juego de caracteres de origen que proporcione debe asignar los caracteres ASCII de 7 bits a los mismos puntos de código en el juego de caracteres, o muchos errores de compilación están probables que siga. El juego de caracteres de origen también debe ser asignable al juego puedan codificarse con UTF-8 de caracteres Unicode extendidos. Caracteres que no se puedan codificar con UTF-8 se representan mediante un sustituto específico de la implementación. El compilador de Microsoft utiliza un signo de interrogación para estos caracteres.  
  
 Si desea establecer el juego de caracteres de origen y el juego de caracteres de ejecución a UTF-8, puede usar el **/utf-8** opción del compilador como un acceso directo. Es equivalente a especificar **/source-charset:utf-/execution 8-charset:utf-8** en la línea de comandos. Cualquiera de estas opciones también habilita la **/validate-charset** opción predeterminada.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración**, **C/C++**, **línea de comandos** carpeta.  
  
3.  En **opciones avanzadas**, agregue el **/source-charset** opción y especifique la codificación preferida.  
  
4.  Elija **Aceptar** para guardar los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/Execution-CharSet (establecer el juego de caracteres en la ejecución)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/UTF-8 (establecer origen y el ejecutable juegos de caracteres UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate/charset (Validar los caracteres compatibles)](../../build/reference/validate-charset-validate-for-compatible-characters.md)