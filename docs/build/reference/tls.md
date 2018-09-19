---
title: -TLS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78f485a783dbe8b5fe9a49ed3100754115bf50b8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714680"
---
# <a name="tls"></a>/TLS

Muestra la estructura IMAGE_TLS_DIRECTORY de un archivo ejecutable.

## <a name="remarks"></a>Comentarios

/ TLS muestra los campos de la estructura TLS, así como las direcciones de las funciones de devolución de llamada TLS.

Si un programa no utiliza almacenamiento local de subprocesos, su imagen no contendrá una estructura TLS.  Consulte [subproceso](../../cpp/thread.md) para obtener más información.

IMAGE_TLS_DIRECTORY se define en winnt.h.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)