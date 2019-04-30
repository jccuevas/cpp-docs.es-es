---
title: Error irrecuperable del compilador de recursos RC1015
ms.date: 11/04/2016
f1_keywords:
- RC1015
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
ms.openlocfilehash: f20101c2edc4da132c89dcda451c71af2304a13d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297663"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Error irrecuperable del compilador de recursos RC1015

no puede abrir el archivo 'filename' include

El archivo de inclusión especificado no existe, no se pudo abrir o no se encontró.

Asegúrese de que la configuración del entorno es válida y de que se especifica la ruta de acceso correcta para el archivo. Asegúrese de que están disponibles para el compilador de recursos suficientes identificadores de archivo. Si el archivo está en una unidad de red, asegúrese de que tiene permisos para abrir el archivo.

RC1015 puede producirse incluso si existe el archivo de inclusión en un directorio especificado como directorio de inclusión adicional en las propiedades de configuración -> recursos -> página de propiedades General; Especifique la ruta de acceso completa al archivo de inclusión.
