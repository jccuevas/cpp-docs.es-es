---
title: Las herramientas del vinculador LNK2039 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2039
dev_langs: C++
helpviewer_keywords: LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 441765d85ce65a80102ed94b3f4394ae48c0e29f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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