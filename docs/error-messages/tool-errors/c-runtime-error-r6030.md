---
title: R6030 de Error en tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae8eb17fc9d074604586582be08c43289b680b4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299541"
---
# <a name="c-runtime-error-r6030"></a>R6030 de Error en tiempo de ejecución de C
CRT no inicializado  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Este problema suele estar provocado por determinados programas de software de seguridad o, en contadas ocasiones, a un error en el programa.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   El software de seguridad puede tener instrucciones específicas para mitigar este problema. Compruebe el sitio Web de su proveedor de software de seguridad para obtener más información. O bien, busque las versiones actualizadas de su software de seguridad o pruebe el software de seguridad diferente.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este error se produce si se usa en tiempo de ejecución de C (CRT), pero no se ejecutó el código de inicio de CRT. Es posible obtener este error si cambia el vinculador [/Entry](../../build/reference/entry-entry-point-symbol.md) se usa para invalidar el valor predeterminado de dirección inicial y normalmente **mainCRTStartup**, **wmainCRTStartup** para un consola EXE, **WinMainCRTStartup** o **wWinMainCRTStartup** para un ejecutable de Windows, o **_DllMainCRTStartup** para un archivo DLL. A menos que se llama a uno de las funciones anteriores en el inicio, el tiempo de ejecución de C no se inicializará. Normalmente se llaman a estas funciones de inicio de forma predeterminada al vincular a la biblioteca en tiempo de ejecución de C y utiliza la normal **principal**, **wmain**, **WinMain**, o  **DllMain** puntos de entrada.  
  
 También es posible obtener este error cuando otro programa usa técnicas de inyección de código para interceptar determinadas llamadas de la biblioteca DLL. Algunos programas de seguridad intrusivo utilizan esta técnica. En versiones de Visual C++ antes de Visual Studio 2015, es posible utilizar una biblioteca de CRT vinculado estáticamente para solucionar el problema, pero esto no se recomienda por motivos de seguridad y aplicación de actualizaciones. Cómo corregir este problema puede requerir la acción del usuario final.