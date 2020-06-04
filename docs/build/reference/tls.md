---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 751c212398f3d309b1d31d204291fe3a0503cf06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317268"
---
# <a name="tls"></a>/TLS

Muestra la estructura IMAGE_TLS_DIRECTORY de un archivo ejecutable.

## <a name="remarks"></a>Comentarios

/ TLS muestra los campos de la estructura TLS, así como las direcciones de las funciones de devolución de llamada TLS.

Si un programa no utiliza almacenamiento local de subprocesos, su imagen no contendrá una estructura TLS.  Consulte [subproceso](../../cpp/thread.md) para obtener más información.

IMAGE_TLS_DIRECTORY se define en winnt.h.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](dumpbin-options.md)
