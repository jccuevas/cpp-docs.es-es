---
title: CWaitCursor (clase)
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
ms.openlocfilehash: 7ce81e62ec6498ad84349108b4c4a07090b17de5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323351"
---
# <a name="cwaitcursor-class"></a>CWaitCursor (clase)

Proporciona una manera de una línea de mostrar un cursor de espera, que se muestra normalmente como un reloj de arena, mientras se está realizando una operación larga.

## <a name="syntax"></a>Sintaxis

```
class CWaitCursor
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Construye un `CWaitCursor` de objeto y se muestra el cursor de espera.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CWaitCursor::Restore](#restore)|Restaura el cursor de espera después de que se ha cambiado.|

## <a name="remarks"></a>Comentarios

`CWaitCursor` no tiene una clase base.

Windows buenas prácticas de programación requieren que mostrar un cursor de espera siempre que se va a realizar una operación que tarda bastante tiempo.

Para mostrar un cursor de espera, simplemente defina un `CWaitCursor` variable antes que el código que realiza la operación de larga duración. El constructor del objeto hace que el cursor de espera que se mostrará automáticamente.

Cuando el objeto queda fuera del ámbito (al final del bloque en el que el `CWaitCursor` se declara el objeto), su destructor establece el cursor hasta el cursor anterior. En otras palabras, el objeto realiza automáticamente la limpieza necesaria.

> [!NOTE]
>  Debido a sus constructores y destructores de funcionan, `CWaitCursor` objetos siempre se declaran como variables locales, nunca se declaran como variables globales ni se asignan con **nuevo**.

Si realiza una operación que puede provocar que el cursor, como mostrar un cuadro de mensaje o cuadro de diálogo, llame al cambiarse la [restaurar](#restore) función miembro para restaurar el cursor de espera. No pasa nada por llamar a `Restore` incluso cuando se muestra actualmente un cursor de espera.

Otra manera de mostrar un cursor de espera es usar la combinación de [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)y quizás [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Sin embargo, `CWaitCursor` es más fácil de usar porque no es necesario establecer el cursor hasta el cursor anterior cuando haya terminado con la operación de larga duración.

> [!NOTE]
>  MFC establece o restablece el cursor mediante la [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) función virtual. Puede reemplazar esta función para proporcionar un comportamiento personalizado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CWaitCursor`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

##  <a name="cwaitcursor"></a>  CWaitCursor::CWaitCursor

Para mostrar un cursor de espera, solo tiene que declarar una `CWaitCursor` objeto antes de que el código que realiza la operación de larga duración.

```
CWaitCursor();
```

### <a name="remarks"></a>Comentarios

El constructor hace que el cursor de espera que se mostrará automáticamente.

Cuando el objeto queda fuera del ámbito (al final del bloque en el que el `CWaitCursor` se declara el objeto), su destructor establece el cursor hasta el cursor anterior. En otras palabras, el objeto realiza automáticamente la limpieza necesaria.

Puede aprovechar el hecho de que se llama al destructor al final del bloque (que puede ser antes del final de la función) para que el cursor de espera activa sólo una parte de la función. Esta técnica se muestra en el segundo ejemplo siguiente.

> [!NOTE]
>  Debido a sus constructores y destructores de funcionan, `CWaitCursor` objetos siempre se declaran como variables locales, nunca se declaran como variables globales, ni se asignan con **nuevo**.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

##  <a name="restore"></a>  CWaitCursor::Restore

Para restaurar el cursor de espera, llame a esta función después de realizar una operación, como mostrar un cuadro de mensaje o cuadro de diálogo, que puede cambiar el cursor de espera a otro cursor.

```
void Restore();
```

### <a name="remarks"></a>Comentarios

Está bien para llamar a `Restore` incluso cuando se muestra actualmente el cursor de espera.

Si tiene que restaurar el cursor de espera mientras se encuentra en una función distinta de aquella en la que el `CWaitCursor` se declara el objeto, puede llamar a [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[¿Cómo lo hago?: Cambiar el Cursor del Mouse en una aplicación de la clase Microsoft Foundation](http://go.microsoft.com/fwlink/p/?linkid=128044)
