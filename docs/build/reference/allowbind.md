---
title: -ALLOWBIND | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /allowbind
dev_langs: C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4cbd5c619b0a9e146adb9a8ec9117f59e01b89d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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