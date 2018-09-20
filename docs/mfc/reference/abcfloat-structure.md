---
title: ABCFLOAT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9bbece0773c14a4a8b545bc56209bf682e22c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375419"
---
# <a name="abcfloat-structure"></a>ABCFLOAT (Estructura)

El `ABCFLOAT` estructura contiene los anchos de A, B y C de un carácter de la fuente.

## <a name="syntax"></a>Sintaxis

```
typedef struct _ABCFLOAT { /* abcf */
    FLOAT abcfA;
    FLOAT abcfB;
    FLOAT abcfC;
} ABCFLOAT;
```

#### <a name="parameters"></a>Parámetros

*abcfA*<br/>
Especifica el espaciado entre un carácter. El espaciado A es la distancia a agregar a la posición actual antes de dibujar el glifo de caracteres.

*abcfB*<br/>
Especifica el espaciado de B del carácter. El espaciado de B es el ancho de la parte dibujar del glifo de caracteres.

*abcfC*<br/>
Especifica el espaciado de C del carácter. El espaciado de C es la distancia a agregar a la posición actual para proporcionar a la derecha del glifo de caracteres de espacio en blanco.

## <a name="remarks"></a>Comentarios

Los anchos de A, B y C se miden a lo largo de la línea de base de la fuente. El incremento de carácter (ancho total) de un carácter es la suma de los espacios A, B y C. La A o el espacio de C puede ser negativo para indicar underhangs o partes sobresalientes.

## <a name="requirements"></a>Requisitos

**Encabezado:** wingdi.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

