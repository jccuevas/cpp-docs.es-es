---
title: COMPAREITEMSTRUCT (Estructura)
ms.date: 11/04/2016
f1_keywords:
- COMPAREITEMSTRUCT
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
ms.openlocfilehash: 78a6e76ee3bbac5b32eb4bccf45578e63f763b75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465421"
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT (Estructura)

El `COMPAREITEMSTRUCT` estructura proporciona los identificadores y los datos proporcionados por la aplicación para los dos elementos en un cuadro de lista dibujado por el propietario y ordenada o cuadro combinado.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagCOMPAREITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    HWND hwndItem;
    UINT itemID1;
    DWORD itemData1;
    UINT itemID2;
    DWORD itemData2;
} COMPAREITEMSTRUCT;
```

#### <a name="parameters"></a>Parámetros

*CtlType*<br/>
Odt_combobox (que especifica un cuadro de lista dibujado por el propietario) o ODT_COMBOBOX (que especifica un cuadro de cuadro combinado dibujado por el propietario).

*CtlID*<br/>
Identificador del control de cuadro de lista o cuadro combinado.

*hwndItem*<br/>
El identificador de ventana del control.

*itemID1*<br/>
El índice del primer elemento en el cuadro de lista o cuadro combinado que se están comparando.

*itemData1*<br/>
Datos proporcionados por la aplicación para el primer elemento que se va a comparar. Este valor se pasa en la llamada que se agregó el elemento al cuadro combinado o lista.

*itemID2*<br/>
Índice del segundo elemento en el cuadro de lista o cuadro combinado que se están comparando.

*itemData2*<br/>
Datos proporcionados por la aplicación para el segundo elemento que se va a comparar. Este valor se pasa en la llamada que se agregó el elemento al cuadro combinado o lista.

## <a name="remarks"></a>Comentarios

Cada vez que una aplicación agrega un nuevo elemento a un cuadro de lista dibujado por el propietario o el cuadro combinado creada con el estilo CBS_SORT o LBS_SORT, Windows envía al propietario de un mensaje WM_COMPAREITEM. El *lParam* parámetro del mensaje contiene un puntero largo a un `COMPAREITEMSTRUCT` estructura. Al recibir el mensaje, el propietario compara los dos elementos y devuelve un valor que indica qué elemento se ordena antes que el otro.

## <a name="requirements"></a>Requisitos

**Encabezado:** winuser.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

