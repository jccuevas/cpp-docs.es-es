---
title: -Fi (Preprocesar el nombre de archivo de salida) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fi
dev_langs:
- C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e7fe5ffbb8a6ccdd5ef02d2cf3feb6b94d48233
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (Preprocesar el nombre del archivo de salida)
Especifica el nombre del archivo de salida a la que el [/P (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) opción del compilador escribe la salida preprocesada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Fipathname  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`pathname`|El nombre y la ruta de acceso del archivo de salida generan por la **/P** opción del compilador.|  
  
## <a name="remarks"></a>Comentarios  
 Use la **/Fi** opción del compilador en combinación con la **/P** opción del compilador.  
  
 Si especifica solo una ruta de acceso para el `pathname` parámetro, el nombre base del archivo de origen se utiliza como el nombre base del archivo de salida preprocesado. El `pathname` parámetro no requiere una extensión de nombre de archivo en particular. Sin embargo, una extensión de "i" se utiliza si no especifica una extensión de nombre de archivo.  
  
## <a name="example"></a>Ejemplo  
 La línea de comandos siguiente preprocesa PROGRAM.cpp, conserva los comentarios, agrega [#line](../../preprocessor/hash-line-directive-c-cpp.md) directivas y escribe el resultado en el archivo MYPROCESS.i.  
  
```  
CL /P /FiMYPROCESS.I PROGRAM.CPP  
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [/P (Preprocesar y escribir en un archivo)](../../build/reference/p-preprocess-to-a-file.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)