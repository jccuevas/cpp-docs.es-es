---
title: -Fi (Preprocesar el nombre de archivo de salida) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Fi
dev_langs: C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9bc3076a529984358aed16902f509ceb01423f9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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