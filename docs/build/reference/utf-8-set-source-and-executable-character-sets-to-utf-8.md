---
title: utf - 8 (establecer origen y ejecutable juegos a UTF-8 de caracteres) | Documentos de Microsoft
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
- /utf-8
dev_langs:
- C++
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 592cba779113a6658b40d0dc3f855f53fa3d170c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/UTF-8 (establecer origen y el ejecutable juegos de caracteres UTF-8)
Especifica el juego de caracteres de origen y el carácter de ejecución establecido como UTF-8.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/utf-8  
```  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el **/utf-8** opción para especificar juegos de caracteres de origen y de ejecución como codificada mediante UTF-8. Es equivalente a especificar **/source-charset:utf-/execution 8-charset:utf-8** en la línea de comandos. Cualquiera de estas opciones también habilita la **/validate-charset** opción predeterminada. Para obtener una lista de admite identificadores de página de código y los nombres del juego de caracteres, vea [identificadores de página de código](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de origen está en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de origen se codifica utilizando la página de códigos del usuario actual, a menos que haya especificado una página de códigos mediante **/utf-8** o **/source-charset** opción. Visual Studio permite guardar el código fuente de C++ mediante cualquiera de varias codificaciones de caracteres. Para obtener información acerca de los conjuntos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets2.md) en la documentación del lenguaje.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración**, **C/C++**, **línea de comandos** carpeta.  
  
3.  En **opciones avanzadas**, agregue el **/utf-8** opción y especifique la codificación preferida.  
  
4.  Elija **Aceptar** para guardar los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/Execution-CharSet (establecer el juego de caracteres en la ejecución)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/Source-CharSet (conjunto de juego de caracteres de origen)](../../build/reference/source-charset-set-source-character-set.md)   
 [/Validate-CharSet (validar caracteres compatibles)](../../build/reference/validate-charset-validate-for-compatible-characters.md)