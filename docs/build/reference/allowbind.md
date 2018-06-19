---
title: -ALLOWBIND | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af4a9f3d898d0087f0e8e861ccfe72e4adadb1de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368920"
---
# <a name="allowbind"></a>/ALLOWBIND
Especifica si se puede enlazar un archivo DLL.  
  
```  
  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 El **/ALLOWBIND** opción establece un bit en el encabezado de un archivo DLL que le indica a Bind.exe que la imagen se permite enlazar. Enlace puede permitir que una imagen que se cargará más rápido cuando el cargador no tiene rebase y realizar la corrección de la dirección para cada DLL que se hace referencia. Puede que no desee un archivo DLL se enlace si se ha firmado digitalmente, el enlace invalida la firma. Enlace no tiene ningún efecto si la selección aleatoria de diseño de espacio de direcciones (ASLR) está habilitada para la imagen mediante el uso de **/DYNAMICBASE** en versiones de Windows compatibles con ASLR.  
  
 Use **/ALLOWBIND: no** para impedir que el archivo DLL de enlace Bind.exe.  
  
 Para obtener más información, consulte el [/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) opción del vinculador.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)