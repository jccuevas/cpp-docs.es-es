---
title: Exit (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5767f6b08b4adcd3d1a8d367c6286a746eeecec3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412535"
---
# <a name="exit-function"></a>exit (Función)
El **salir** función, declarada en el archivo de inclusión estándar \<stdlib.h >, finaliza un programa de C++.  
  
 El valor proporcionado como argumento pasado a **salir** se devuelve al sistema operativo como código de salida o de código de retorno del programa. Por convención, un código de retorno de cero significa que el programa se completó correctamente.  
  
> [!NOTE]
>  Puede usar las constantes `EXIT_FAILURE` y `EXIT_SUCCESS`, definida en \<stdlib.h >, para indicar el éxito o fracaso del programa.  
  
 Emitir un `return` instrucción desde la **principal** función es equivalente a llamar a la **salir** función con el valor devuelto como argumento.  
  
 Para obtener más información, consulte [salir](../c-runtime-library/reference/exit-exit-exit.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="see-also"></a>Vea también  
 [Finalización del programa](../cpp/program-termination.md)