---
title: Error irrecuperable C1037 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1037
dev_langs:
- C++
helpviewer_keywords:
- C1037
ms.assetid: 79103bca-ccfb-42e7-aef9-9b90c15b162f
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c1f358201b36b73e1db41f2f72e1f92deb44f368
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1037"></a>Error irrecuperable C1037
no se puede abrir el archivo objeto nombreArchivo  
  
 El archivo objeto especificado por [/Fo](../../build/reference/fo-object-file-name.md) no se puede abrir.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Nombre de archivo no válido.  
  
2.  Memoria insuficiente para abrir el archivo.  
  
3.  Otro proceso está usando el archivo.  
  
4.  Un archivo de solo lectura tiene el mismo nombre.  
  
 En Visual C++ .NET (versión 1300 del compilador), hay un error que necesita que la configuración regional del usuario se establezca correctamente cuando el nombre de archivo (o la ruta de acceso del directorio al nombre de archivo) contiene caracteres MBCS. Establecer la configuración regional del sistema no es suficiente; debe establecerse la configuración regional del usuario para procesar caracteres MBCS.
