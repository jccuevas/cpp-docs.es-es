---
title: Error irrecuperable del compilador de recursos RC1015 | Microsoft Docs
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
ms.openlocfilehash: 7a72cba53ebe9a286ac2e7cbbf2c41b78f4e4e08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100771"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Error irrecuperable del compilador de recursos RC1015

no puede abrir el archivo 'filename' include

El archivo de inclusión especificado no existe, no se pudo abrir o no se encontró.

Asegúrese de que la configuración del entorno es válida y de que se especifica la ruta de acceso correcta para el archivo. Asegúrese de que están disponibles para el compilador de recursos suficientes identificadores de archivo. Si el archivo está en una unidad de red, asegúrese de que tiene permisos para abrir el archivo.

RC1015 puede producirse incluso si existe el archivo de inclusión en un directorio especificado como directorio de inclusión adicional en las propiedades de configuración -> recursos -> página de propiedades General; Especifique la ruta de acceso completa al archivo de inclusión.

Para obtener más información, consulte el artículo de Knowledge Base Q326987: RC1015 Error cuando utiliza recursos vista si la ruta de inclusión es demasiado largo.