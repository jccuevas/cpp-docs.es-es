---
title: Clase CWaitCursor
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 48ef8f9c965f54deafcc62451639f8c31021e900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373174"
---
# <a name="cwaitcursor-class"></a>Clase CWaitCursor

Proporciona una manera de una línea de mostrar un cursor de espera, que se muestra normalmente como un reloj de arena, mientras se está realizando una operación larga.

## <a name="syntax"></a>Sintaxis

```
class CWaitCursor
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Construye un `CWaitCursor` objeto y muestra el cursor de espera.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWaitCursor::Restaurar](#restore)|Restaura el cursor de espera después de cambiarlo.|

## <a name="remarks"></a>Observaciones

`CWaitCursor`no tiene una clase base.

Las buenas prácticas de programación de Windows requieren que muestre un cursor de espera cada vez que realice una operación que tarde un tiempo notable.

Para mostrar un cursor de `CWaitCursor` espera, simplemente defina una variable antes del código que realiza la operación larga. El constructor del objeto hace que se muestre automáticamente el cursor de espera.

Cuando el objeto sale del ámbito (al final `CWaitCursor` del bloque en el que se declara el objeto), su destructor establece el cursor en el cursor anterior. En otras palabras, el objeto realiza automáticamente la limpieza necesaria.

> [!NOTE]
> Debido a cómo funcionan sus constructores y destructores, `CWaitCursor` los objetos siempre se declaran como variables locales: nunca se declaran como variables globales ni se asignan con **new**.

Si realiza una operación que puede hacer que se cambie el cursor, como mostrar un cuadro de mensaje o un cuadro de diálogo, llame a la [Restaurar](#restore) función miembro para restaurar el cursor de espera. Está bien llamar `Restore` incluso cuando se muestra un cursor de espera actualmente.

Otra forma de mostrar un cursor de espera es utilizar la combinación de [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)y quizás [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Sin `CWaitCursor` embargo, es más fácil de usar porque no es necesario establecer el cursor en el cursor anterior cuando haya terminado con la operación larga.

> [!NOTE]
> MFC establece y restaura el cursor mediante la función virtual [CWinApp::DoWaitCursor.](../../mfc/reference/cwinapp-class.md#dowaitcursor) Puede invalidar esta función para proporcionar un comportamiento personalizado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CWaitCursor`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor::CWaitCursor

Para mostrar un cursor de `CWaitCursor` espera, simplemente declare un objeto antes del código que realiza la operación larga.

```
CWaitCursor();
```

### <a name="remarks"></a>Observaciones

El constructor hace que se muestre automáticamente el cursor de espera.

Cuando el objeto sale del ámbito (al final `CWaitCursor` del bloque en el que se declara el objeto), su destructor establece el cursor en el cursor anterior. En otras palabras, el objeto realiza automáticamente la limpieza necesaria.

Puede aprovechar el hecho de que se llama al destructor al final del bloque (que podría estar antes del final de la función) para activar el cursor de espera solo en una parte de la función. Esta técnica se muestra en el segundo ejemplo a continuación.

> [!NOTE]
> Debido a cómo funcionan sus constructores y destructores, `CWaitCursor` los objetos siempre se declaran como variables locales: nunca se declaran como variables globales, ni se asignan con **new**.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor::Restaurar

Para restaurar el cursor de espera, llame a esta función después de realizar una operación, como mostrar un cuadro de mensaje o un cuadro de diálogo, que podría cambiar el cursor de espera a otro cursor.

```
void Restore();
```

### <a name="remarks"></a>Observaciones

Está bien llamar `Restore` incluso cuando se muestra el cursor de espera actualmente.

Si necesita restaurar el cursor de espera mientras se `CWaitCursor` encuentra en una función distinta de la en la que se declara el objeto, puede llamar a [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Cómo puedo: cambiar el cursor del ratón en una aplicación de Microsoft Foundation Class](https://go.microsoft.com/fwlink/p/?linkid=128044)
