---
title: Las herramientas del vinculador LNK2039 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 954ea12eb9b49c2bdf59b31a1ec2ec2e66c124ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302102"
---
# <a name="linker-tools-error-lnk2039"></a>Error de las herramientas del vinculador LNK2039
importación de la clase ref\<tipo >' que se define en another.obj; debe ser importados o definido, pero no ambos  
  
 La clase ref ' <`type`>' se importa en el archivo .obj especificado, pero también se define en otro archivo de obj. Esta condición puede provocar errores en tiempo de ejecución u otro comportamiento inesperado.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Compruebe si '`type`' debe definirse en el otro archivo .obj y compruebe si se debe importar desde el archivo .winmd.  
  
2.  Quite la definición o la importación.  
  
## <a name="see-also"></a>Vea también  
 [Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [Error de las herramientas del vinculador LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)