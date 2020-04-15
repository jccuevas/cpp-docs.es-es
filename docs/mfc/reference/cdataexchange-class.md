---
title: Clase CDataExchange
ms.date: 11/04/2016
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: 73319ad898bfebf4caf191954ebb3935bd4ebce9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321966"
---
# <a name="cdataexchange-class"></a>Clase CDataExchange

Admite rutinas de intercambio de datos de cuadros de diálogo (DDX) y de validación de datos de cuadros de diálogo (DDV) utilizadas por las clases de Microsoft Foundation.

## <a name="syntax"></a>Sintaxis

```
class CDataExchange
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDataExchange::CDataExchange](#cdataexchange)|Construye un objeto `CDataExchange`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDataExchange::Fail](#fail)|Se llama cuando se produce un error en la validación. Restablece el foco al control anterior y produce una excepción.|
|[CDataExchange::PrepareCtrl](#preparectrl)|Prepara el control especificado para el intercambio o la validación de datos. Se utiliza para controles no edita.|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Prepara el control de edición especificado para el intercambio o la validación de datos.|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Prepara el control OLE especificado para el intercambio o validación de datos. Se utiliza para controles no edita.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Marcador para la dirección de DDX y DDV.|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|El cuadro de diálogo o la ventana donde tiene lugar el intercambio de datos.|

## <a name="remarks"></a>Observaciones

`CDataExchange`no tiene una clase base.

Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos o controles personalizados, o si está escribiendo sus propias rutinas de validación de datos. Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, consulte la [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general sobre DDX y DDV, vea Intercambio de datos de cuadro de [diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y [cuadros](../../mfc/dialog-boxes.md)de diálogo .

Un `CDataExchange` objeto proporciona la información de contexto necesaria para dDX y DDV que se llevará a cabo. El *m_bSaveAndValidate* de marca es FALSE cuando se usa DDX para rellenar los valores iniciales de los controles de cuadro de diálogo de los miembros de datos. La *marca m_bSaveAndValidate* es TRUE cuando se utiliza DDX para establecer los valores actuales de los controles de cuadro de diálogo en miembros de datos y cuando se usa DDV para validar los valores de datos. Si se produce un error en la validación de DDV, el procedimiento DDV mostrará un cuadro de mensaje que explica el error de entrada. A continuación, el `Fail` procedimiento DDV llamará para restablecer el foco en el control infractor y producirá una excepción para detener el proceso de validación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDataExchange`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a>CDataExchange::CDataExchange

Llame a esta función miembro para construir un `CDataExchange` objeto.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Parámetros

*pDlgWnd*<br/>
Puntero a la ventana primaria que contiene el control. Normalmente se trata de un [CDialog](../../mfc/reference/cdialog-class.md)-objeto derivado.

*bSaveAndValidate*<br/>
Si TRUE, este objeto valida los datos y, a continuación, escribe datos de los controles a los miembros. Si FALSE, este objeto moverá datos de los miembros a los controles.

### <a name="remarks"></a>Observaciones

Construir `CDataExchange` un objeto usted mismo para almacenar información adicional en el objeto de intercambio de datos para pasar a la ventana [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a>CDataExchange::Fail

El marco de trabajo llama a esta función miembro cuando se produce un error en una operación de validación de datos de cuadro de diálogo (DDV).

```
void Fail();
```

### <a name="remarks"></a>Observaciones

`Fail`restaura el foco y la selección al control cuya validación ha fallado (si hay un control que se va a restaurar). `Fail`a continuación, produce una excepción de tipo [CUserException](../../mfc/reference/cuserexception-class.md) para detener el proceso de validación. La excepción hace que se muestre un cuadro de mensaje que explica el error. Después de que se produzca un error en la validación de DDV, el usuario puede volver a escribir datos en el control infractor.

Los implementadores de rutinas DDV personalizadas pueden llamar `Fail` desde sus rutinas cuando se produce un error en una validación.

Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, consulte la [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general sobre DDX y DDV, vea Intercambio de datos de cuadro de [diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y temas de cuadro de [diálogo](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate

Este indicador indica la dirección de una operación de intercambio de datos de cuadro de diálogo (DDX).

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Observaciones

El indicador es distinto `CDataExchange` de cero si el objeto se utiliza para mover datos de los controles de cuadro de diálogo a los miembros de datos de clase de cuadro de diálogo después de que el usuario edita los controles. El indicador es cero si el objeto se utiliza para inicializar controles de cuadro de diálogo de miembros de datos de clase de cuadro de diálogo.

El indicador también es distinto de cero durante la validación de datos de cuadro de diálogo (DDV).

Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, consulte la [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general sobre DDX y DDV, vea Intercambio de datos de cuadro de [diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y temas de cuadro de [diálogo](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd

Contiene un puntero al objeto [CWnd](../../mfc/reference/cwnd-class.md) para el que se está llevando a cabo el intercambio de datos de cuadro de diálogo (DDX) o la validación (DDV).

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Observaciones

Este objeto suele ser un [CDialog](../../mfc/reference/cdialog-class.md) objeto. Los implementadores de rutinas DDX o DDV personalizadas pueden usar este puntero para obtener acceso a la ventana de diálogo que contiene los controles en los que están operando.

Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, consulte la [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general sobre DDX y DDV, vea Intercambio de datos de cuadro de [diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y temas de cuadro de [diálogo](../../mfc/dialog-boxes.md).

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a>CDataExchange::PrepareCtrl

El marco de trabajo llama a esta función miembro para preparar el control especificado para el intercambio de datos de cuadro de diálogo (DDX) y la validación (DDV).

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Parámetros

*nIDC*<br/>
El identificador del control que se va a preparar para DDX o DDV.

### <a name="return-value"></a>Valor devuelto

El HWND del control que se está preparando para DDX o DDV.

### <a name="remarks"></a>Observaciones

Utilice [PrepareEditCtrl](#prepareeditctrl) en su lugar para los controles de edición; utilizar esta función miembro para todos los demás controles.

La preparación consiste en almacenar el `CDataExchange` HWND del control en la clase. El marco de trabajo usa este identificador para restaurar el foco en el control centrado anteriormente en caso de un error de DDX o DDV.

Los implementadores de rutinas DDX o `PrepareCtrl` DDV personalizadas deben llamar a todos los controles que no son de edición para los que intercambian datos a través de DDX o validan datos a través de DDV.

Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, consulte la [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general sobre DDX y DDV, vea Intercambio de datos de cuadro de [diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y temas de cuadro de [diálogo](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl

El marco de trabajo llama a esta función miembro para preparar el control de edición especificado para el intercambio de datos de cuadro de diálogo (DDX) y la validación (DDV).

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Parámetros

*nIDC*<br/>
El identificador del control de edición que se va a preparar para DDX o DDV.

### <a name="return-value"></a>Valor devuelto

El HWND del control de edición que se está preparando para DDX o DDV.

### <a name="remarks"></a>Observaciones

Utilice [PrepareCtrl](#preparectrl) en su lugar para todos los controles que no sean de edición.

La preparación consta de dos cosas. En `PrepareEditCtrl` primer lugar, almacena el `CDataExchange` HWND del control en la clase. El marco de trabajo usa este identificador para restaurar el foco en el control centrado anteriormente en caso de un error de DDX o DDV. En `PrepareEditCtrl` segundo lugar, `CDataExchange` establece un indicador en la clase para indicar que el control cuyos datos se intercambian o validan es un control de edición.

Los implementadores de rutinas DDX o `PrepareEditCtrl` DDV personalizadas deben llamar a todos los controles de edición para los que intercambian datos a través de DDX o validan datos a través de DDV.

Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, consulte la [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general sobre DDX y DDV, vea Intercambio de datos de cuadro de [diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y temas de cuadro de [diálogo](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl

El marco de trabajo llama a esta función miembro para preparar el control OLE especificado para el intercambio de datos de cuadro de diálogo (DDX) y la validación (DDV).

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Parámetros

*nIDC*<br/>
El identificador del control OLE que se va a preparar para DDX o DDV.

### <a name="return-value"></a>Valor devuelto

Un puntero al sitio de control OLE.

### <a name="remarks"></a>Observaciones

Utilice [PrepareEditCtrl](#prepareeditctrl) en su lugar para los controles de edición o [PrepareCtrl](#preparectrl) para todos los demás controles no OLE.

Los implementadores de rutinas DDX o `PrepareOleCtrl` DDV personalizadas deben llamar a todos los controles OLE para los que intercambian datos a través de DDX o validan datos a través de DDV.

Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, consulte la [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general sobre DDX y DDV, vea Intercambio de datos de cuadro de [diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y temas de cuadro de [diálogo](../../mfc/dialog-boxes.md).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
