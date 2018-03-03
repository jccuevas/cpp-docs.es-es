---
title: Error irrecuperable del compilador de recursos RC1015 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 666221cf5c3e812cd856271ea97cf4966383ec20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Error irrecuperable del compilador de recursos RC1015
no puede abrir el archivo 'filename' de inclusión  
  
 El archivo de inclusión especificado no existe, no se pudo abrir o no se encontró.  
  
 Asegúrese de que la configuración del entorno es válida y de que se especifica la ruta de acceso correcta para el archivo. Asegúrese de que están disponibles para el compilador de recursos suficientes identificadores de archivo. Si el archivo está en una unidad de red, asegúrese de que tiene permisos para abrir el archivo.  
  
 Error RC1015 puede producirse incluso si el archivo de inclusión existe en un directorio especificado como directorio de inclusión adicional en las propiedades de configuración -> recursos -> página de propiedades General; Especifique la ruta de acceso completa al archivo de inclusión.  
  
 Para obtener más información, vea el artículo de Knowledge Base Q326987: del RC1015 Error al usar recursos vista si la ruta de acceso de inclusión es demasiado largo.