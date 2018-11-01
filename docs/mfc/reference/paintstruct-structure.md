---
title: PAINTSTRUCT (Estructura)
ms.date: 11/04/2016
f1_keywords:
- PAINTSTRUCT
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
ms.openlocfilehash: b5179a1bcba4a654ff235885ec2d0516e801fbb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677128"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT (Estructura)

El `PAINTSTRUCT` estructura contiene información que puede utilizarse para pintar el área cliente de una ventana.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagPAINTSTRUCT {
    HDC hdc;
    BOOL fErase;
    RECT rcPaint;
    BOOL fRestore;
    BOOL fIncUpdate;
    BYTE rgbReserved[16];
} PAINTSTRUCT;
```

#### <a name="parameters"></a>Parámetros

*HDC*<br/>
Identifica el contexto de presentación que se utiliza para dibujar.

*fErase*<br/>
Especifica si se debe volver a dibujar el fondo. No es 0 si la aplicación debe volver a dibujar el fondo. La aplicación es responsable de dibujar el fondo, si se crea una clase de ventana de Windows sin un pincel de fondo (vea la descripción de la `hbrBackground` miembro de la [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) estructura en el SDK de Windows).

*rcPaint*<br/>
Especifica la esquina superior izquierda esquinas e inferior derecha del rectángulo en el que se solicita la pintura.

*fRestore*<br/>
Miembro reservado. Se usa internamente por Windows.

*fIncUpdate*<br/>
Miembro reservado. Se usa internamente por Windows.

*rgbReserved [16]*<br/>
Miembro reservado. Un bloque de memoria utilizada internamente por Windows reservado.

## <a name="requirements"></a>Requisitos

**Encabezado:** winuser.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

