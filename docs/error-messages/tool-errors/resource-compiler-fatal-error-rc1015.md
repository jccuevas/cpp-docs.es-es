---
title: Error irrecuperable del compilador de recursos RC1015 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7744242e44ecfc72ee57ab979969ad81b209e57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322827"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Error irrecuperable del compilador de recursos RC1015
no puede abrir el archivo 'filename' de inclusión  
  
 El archivo de inclusión especificado no existe, no se pudo abrir o no se encontró.  
  
 Asegúrese de que la configuración del entorno es válida y de que se especifica la ruta de acceso correcta para el archivo. Asegúrese de que están disponibles para el compilador de recursos suficientes identificadores de archivo. Si el archivo está en una unidad de red, asegúrese de que tiene permisos para abrir el archivo.  
  
 Error RC1015 puede producirse incluso si el archivo de inclusión existe en un directorio especificado como directorio de inclusión adicional en las propiedades de configuración -> recursos -> página de propiedades General; Especifique la ruta de acceso completa al archivo de inclusión.  
  
 Para obtener más información, vea el artículo de Knowledge Base Q326987: del RC1015 Error al usar recursos vista si la ruta de acceso de inclusión es demasiado largo.