---
title: DHtmlUrlEventMapEntry (Estructura)
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: 0a1dc86080c094a7ac89940cd43a8edac973e10c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431634"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry (Estructura)

El `DHtmlUrlEventMapEntry` estructura proporciona compatibilidad con varias direcciones URL el mapa de eventos.

## <a name="syntax"></a>Sintaxis

```
struct DHtmlUrlEventMapEntry
{
LPCTSTR szUrl;
const DHtmlEventMapEntry *pEventMap;
};
```

#### <a name="parameters"></a>Parámetros

*szUrl*<br/>
La dirección URL.

*pEventMap*<br/>
El mapa de eventos asociado con la dirección URL.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdhtml.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

