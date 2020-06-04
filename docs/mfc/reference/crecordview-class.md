---
title: CRecordView (clase)
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: b706a80f91a3c952d80da13f453a807c775b9405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368351"
---
# <a name="crecordview-class"></a>CRecordView (clase)

Una vista que muestra registros de una base de datos en controles.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CRecordView::CRecordView](#crecordview)|Construye un objeto `CRecordView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Devuelve distinto de cero si el registro actual es el primer registro del conjunto de registros asociado.|
|[CRecordView::IsonLastRecord](#isonlastrecord)|Devuelve distinto de cero si el registro actual es el último registro del conjunto de registros asociado.|
|[CRecordView::OnGetRecordset](#ongetrecordset)|Devuelve un puntero a un objeto `CRecordset`de una clase derivada de . ClassWizard reemplaza esta función automáticamente y crea el conjunto de registros si es necesario.|
|[CRecordView::OnMove](#onmove)||

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CRecordView::OnMove](#onmove)|Si el registro actual ha cambiado, lo actualiza en el origen de datos y, a continuación, se mueve al registro especificado (siguiente, anterior, primero o último).|

## <a name="remarks"></a>Observaciones

La vista es una vista `CRecordset` de formulario conectada directamente a un objeto. La vista se crea a partir de un `CRecordset` recurso de plantilla de cuadro de diálogo y muestra los campos del objeto en los controles de la plantilla de cuadro de diálogo. El `CRecordView` objeto utiliza el intercambio de datos de cuadro de diálogo (DDX) y el intercambio de campos de registros (RFX) para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de registros. `CRecordView`también proporciona una implementación predeterminada para pasar al primer, siguiente, anterior o último registro y una interfaz para actualizar el registro actualmente en vista.

> [!NOTE]
> Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de conectividad de base de datos abierta (ODBC), utilice la clase [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) en su lugar. Para obtener más información, consulte el artículo [Información general: Programación](../../data/data-access-programming-mfc-atl.md)de bases de datos .

La forma más común de crear la vista de registros es con el Asistente para aplicaciones. El Asistente para aplicaciones crea la clase de vista de registros y su clase de conjunto de registros asociada como parte de la aplicación de inicio de esqueleto. Si no crea la clase de vista de registros con el Asistente para aplicaciones, puede crearla más adelante con ClassWizard. Si simplemente necesita un único formulario, el enfoque del Asistente para aplicaciones es más fácil. ClassWizard le permite decidir usar una vista de registro más adelante en el proceso de desarrollo. El uso de ClassWizard para crear una vista de registros y un conjunto de registros por separado y, a continuación, conectarlos es el enfoque más flexible porque proporciona más control en el nombre de la clase de conjunto de registros y su . H/. Archivos CPP. Este enfoque también le permite tener varias vistas de registros en la misma clase de conjunto de registros.

Para facilitar a los usuarios finales pasar de un registro a otro en la vista de registros, el Asistente para aplicaciones crea recursos de menú (y, opcionalmente, barra de herramientas) para pasar al primer, siguiente, anterior o último registro. Si crea una clase de vista de registros con ClassWizard, debe crear estos recursos usted mismo con los editores de menú y mapa de bits.

Para obtener información acerca de la implementación `IsOnFirstRecord` `IsOnLastRecord` predeterminada para pasar de un registro a otro, vea y el artículo Uso de [una vista](../../data/using-a-record-view-mfc-data-access.md)de registros .

`CRecordView`realiza un seguimiento de la posición del usuario en el conjunto de registros para que la vista de registros pueda actualizar la interfaz de usuario. Cuando el usuario se mueve a cualquiera de los extremos del conjunto de registros, la vista de registros deshabilita los objetos de la interfaz de usuario, como los elementos de menú o los botones de la barra de herramientas, para avanzar en la misma dirección.

Para obtener más información sobre cómo declarar y usar la vista de registros y las clases de conjunto de registros, vea "Diseñar y crear una vista de registros" en el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros . Para obtener más información sobre cómo funcionan las vistas de registros y cómo usarlas, consulte el artículo Uso de [una vista](../../data/using-a-record-view-mfc-data-access.md)de registros .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>CRecordView::CRecordView

Al crear un objeto de un `CRecordView`tipo derivado de , llame a cualquiera de las formas del constructor para inicializar el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*nIDTemplate*<br/>
Contiene el número de identificador de un recurso de plantilla de cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Puede identificar el recurso por nombre (pasar una cadena como argumento al constructor) o por su identificador (pasar un entero sin signo como argumento). Se recomienda usar un identificador de recurso.

> [!NOTE]
> La clase derivada *debe* proporcionar su propio constructor. En el constructor de la clase `CRecordView::CRecordView` derivada, llame al constructor con el nombre de recurso o el identificador como argumento, como se muestra en el ejemplo siguiente.

`CRecordView::OnInitialUpdate`llamadas `UpdateData`, `DoDataExchange`que llama a . Esta llamada `DoDataExchange` inicial `CRecordView` para conectar controles `CRecordset` (indirectamente) a los miembros de datos de campo creados por ClassWizard. Estos miembros de datos no se `CFormView::OnInitialUpdate` pueden usar hasta después de llamar a la función miembro de clase base.

> [!NOTE]
> Si usa ClassWizard, el asistente define `CRecordView::IDD`un valor **de enumeración** , lo especifica en la declaración de clase y lo usa en la lista de inicialización de miembros para el constructor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CRecordView::IsOnFirstRecord

Llame a esta función miembro para determinar si el registro actual es el primer registro en el objeto de conjunto de registros asociado a esta vista de registro.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro actual es el primer registro del conjunto de registros; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función es útil para escribir sus propias implementaciones de controladores de actualización de comandos predeterminados escritos por ClassWizard.

Si el usuario se mueve al primer registro, el marco de trabajo deshabilita los objetos de interfaz de usuario que tiene para pasar al primer registro o al anterior.

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CRecordView::IsonLastRecord

Llame a esta función miembro para determinar si el registro actual es el último registro en el objeto de conjunto de registros asociado a esta vista de registro.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro actual es el último registro del conjunto de registros; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función es útil para escribir sus propias implementaciones de los controladores de actualización de comandos predeterminados que ClassWizard escribe para admitir una interfaz de usuario para pasar de un registro a otro.

> [!CAUTION]
> El resultado de esta función es confiable, excepto que la vista no puede detectar el final del conjunto de registros hasta que el usuario se haya movido más allá de él. El usuario debe ir más allá del último registro antes de que la vista de registro sintie que debe deshabilitar los objetos de interfaz de usuario para pasar al registro siguiente o al último. Si el usuario pasa el último registro y, a continuación, vuelve al último registro (o antes de él), la vista de registros puede realizar un seguimiento de la posición del usuario en el conjunto de registros y deshabilitar los objetos de interfaz de usuario correctamente. `IsOnLastRecord`también es poco fiable después `OnRecordLast`de una llamada a `CRecordset::MoveLast`la función de implementación , que controla el comando ID_RECORD_LAST, o .

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>CRecordView::OnGetRecordset

Devuelve un puntero `CRecordset`al objeto derivado asociado a la vista de registros.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Valor devuelto

Puntero a `CRecordset`un objeto derivado si el objeto se creó correctamente; de lo contrario, un puntero NULL.

### <a name="remarks"></a>Observaciones

Debe invalidar esta función miembro para construir u obtener un objeto de conjunto de registros y devolver un puntero a él. Si declara la clase de vista de registros con ClassWizard, el asistente escribe una invalidación predeterminada. La implementación predeterminada de ClassWizard devuelve el puntero de conjunto de registros almacenado en la vista de registros si existe uno. Si no es así, construye un objeto de conjunto de `Open` registros del tipo especificado con ClassWizard y llama a su función miembro para abrir la tabla o ejecutar la consulta y, a continuación, devuelve un puntero al objeto.

Para obtener más información y ejemplos, consulte el artículo Vistas de [registros: Uso](../../data/using-a-record-view-mfc-data-access.md)de una vista de registros .

## <a name="crecordviewonmove"></a><a name="onmove"></a>CRecordView::OnMove

Llame a esta función miembro para desplazarse a un registro diferente en el conjunto de registros y mostrar sus campos en los controles de la vista de registros.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parámetros

*nIDMoveCommand*<br/>
Uno de los siguientes valores de ID de comando estándar:

- ID_RECORD_FIRST Mover al primer registro del conjunto de registros.

- ID_RECORD_LAST Mover al último registro del conjunto de registros.

- ID_RECORD_NEXT Mover al siguiente registro del conjunto de registros.

- ID_RECORD_PREV Mover al registro anterior en el conjunto de registros.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el movimiento se realizó correctamente; de lo contrario 0 si la solicitud de mudanza fue denegada.

### <a name="remarks"></a>Observaciones

La implementación predeterminada `Move` llama a `CRecordset` la función miembro adecuada del objeto asociado a la vista de registros.

De forma `OnMove` predeterminada, actualiza el registro actual en el origen de datos si el usuario lo ha cambiado en la vista de registros.

El Asistente para aplicaciones crea un recurso de menú con los elementos de menú Primer registro, Ultimo registro, Siguiente registro y Registro anterior. Si selecciona la opción Barra de herramientas acoplable, el Asistente para aplicaciones también crea una barra de herramientas con botones correspondientes a estos comandos.

Si pasa el último registro del conjunto de registros, la vista de registros continúa mostrando el último registro. Si retrocede más allá del primer registro, la vista de registro continúa mostrando el primer registro.

> [!CAUTION]
> Al `OnMove` llamar se produce una excepción si el conjunto de registros no tiene registros. Llame a la función `OnUpdateRecordFirst`de `OnUpdateRecordLast` `OnUpdateRecordNext`controlador `OnUpdateRecordPrev` de actualización de la interfaz de usuario adecuada (, , , , o) antes de la operación de movimiento correspondiente para determinar si el conjunto de registros tiene registros.

## <a name="see-also"></a>Consulte también

[Clase CFormView](../../mfc/reference/cformview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Clase CFormView](../../mfc/reference/cformview-class.md)
