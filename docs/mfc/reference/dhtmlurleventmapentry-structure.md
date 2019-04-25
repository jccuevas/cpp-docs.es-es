---
title: DHtmlUrlEventMapEntry (Estructura)
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: c9b58067a9c8b6a71cd22b654a2f82ba0f8bfe36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322740"
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
