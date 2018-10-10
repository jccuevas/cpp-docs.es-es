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
ms.openlocfilehash: 0456845152fb2879d2f58c9c40af2562c7207535
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890249"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Error irrecuperable del compilador de recursos RC1015

no puede abrir el archivo 'filename' include

El archivo de inclusión especificado no existe, no se pudo abrir o no se encontró.

Asegúrese de que la configuración del entorno es válida y de que se especifica la ruta de acceso correcta para el archivo. Asegúrese de que están disponibles para el compilador de recursos suficientes identificadores de archivo. Si el archivo está en una unidad de red, asegúrese de que tiene permisos para abrir el archivo.

RC1015 puede producirse incluso si existe el archivo de inclusión en un directorio especificado como directorio de inclusión adicional en las propiedades de configuración -> recursos -> página de propiedades General; Especifique la ruta de acceso completa al archivo de inclusión.
