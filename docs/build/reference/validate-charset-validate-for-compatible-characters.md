---
title: -validar-charset (validar caracteres compatibles) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /validate-charset
- validate-charset
dev_langs:
- C++
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7694eb94fe1b50d1892dab399b523a5b0e6deef7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/Validate-CharSet (validar caracteres compatibles)
Valida que el texto del archivo de origen contiene solo caracteres representables como UTF-8.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/validate-charset[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el **/validate-charset** opción para validar que el código fuente contiene solo el configuran de caracteres que se pueden representar en el carácter de origen y conjunto de caracteres de la ejecución. Esta comprobación se habilita automáticamente cuando se especifica **/source-charset**, **/execution-charset**, o **/utf-8** opciones del compilador. También puede deshabilitar explícitamente esta comprobación especificando el **/ validate-charset -** opción.  
  
 De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de origen está en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de origen se codifica utilizando la página de códigos del usuario actual, a menos que haya especificado una página de códigos mediante **/utf-8** o **/source-charset** opción. Visual Studio permite guardar el código fuente de C++ mediante cualquiera de varias codificaciones de caracteres. Para obtener información acerca de los conjuntos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets2.md) en la documentación del lenguaje. Para obtener una lista de admite identificadores de página de código y los nombres del juego de caracteres, vea [identificadores de página de código](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Visual Studio usa UTF-8 como la codificación de caracteres interno durante la conversión entre el juego de caracteres de origen y el juego de caracteres de ejecución. Si no se puede representar un carácter en el archivo de origen en el juego de caracteres de ejecución, la conversión de UTF-8 se sustituye por un signo de interrogación '?' caracteres. El **/validate-charset** opción hace que la compilación notificar una advertencia en este caso.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración**, **C/C++**, **línea de comandos** carpeta.  
  
3.  En **opciones avanzadas**, agregue el **/validate-charset** opción y especifique la codificación preferida.  
  
4.  Elija **Aceptar** para guardar los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/Execution-CharSet (establecer el juego de caracteres en la ejecución)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/Source-CharSet (conjunto de juego de caracteres de origen)](../../build/reference/source-charset-set-source-character-set.md)   
 [/utf-8 (Establecer los juegos de caracteres de ejecución y origen en UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)