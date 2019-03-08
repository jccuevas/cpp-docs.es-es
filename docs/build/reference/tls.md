---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 1760e94046a950f67d3c3fd7ef13aa40ca7de47a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417793"
---
# <a name="tls"></a>/TLS

Muestra la estructura IMAGE_TLS_DIRECTORY de un archivo ejecutable.

## <a name="remarks"></a>Comentarios

/ TLS muestra los campos de la estructura TLS, así como las direcciones de las funciones de devolución de llamada TLS.

Si un programa no utiliza almacenamiento local de subprocesos, su imagen no contendrá una estructura TLS.  Consulte [subproceso](../../cpp/thread.md) para obtener más información.

IMAGE_TLS_DIRECTORY se define en winnt.h.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)
