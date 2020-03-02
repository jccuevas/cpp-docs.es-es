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
ms.openlocfilehash: 409739d97c9f7ae9a730ac8f05bd86e647da2c71
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215533"
---
# <a name="crecordview-class"></a>CRecordView (clase)

Una vista que muestra registros de una base de datos en controles.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[CRecordView:: CRecordView](#crecordview)|Construye un objeto `CRecordView`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRecordView:: IsOnFirstRecord](#isonfirstrecord)|Devuelve un valor distinto de cero si el registro actual es el primer registro del conjunto de registros asociado.|
|[CRecordView:: IsOnLastRecord](#isonlastrecord)|Devuelve un valor distinto de cero si el registro actual es el último registro del conjunto de registros asociado.|
|[CRecordView:: OnGetRecordset](#ongetrecordset)|Devuelve un puntero a un objeto de una clase derivada de `CRecordset`. ClassWizard invalida esta función automáticamente y crea el conjunto de registros si es necesario.|
|[CRecordView:: Move](#onmove)||

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CRecordView:: Move](#onmove)|Si el registro actual ha cambiado, lo actualiza en el origen de datos y, a continuación, se mueve al registro especificado (siguiente, anterior, primero o último).|

## <a name="remarks"></a>Comentarios

La vista es una vista de formulario conectada directamente a un objeto `CRecordset`. La vista se crea a partir de un recurso de plantilla de cuadro de diálogo y muestra los campos del objeto `CRecordset` en los controles de la plantilla de cuadro de diálogo. El objeto `CRecordView` usa el intercambio de datos de cuadros de diálogo (DDX) y el intercambio de campos de registros (RFX) para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de registros. `CRecordView` también proporciona una implementación predeterminada para moverse al primer, siguiente, anterior o último registro y una interfaz para actualizar el registro que se encuentra actualmente en la vista.

> [!NOTE]
>  Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de conectividad abierta de bases de datos (ODBC), use la clase [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) en su lugar. Para obtener más información, vea el artículo [información general sobre la programación de bases de datos](../../data/data-access-programming-mfc-atl.md).

La forma más común de crear la vista de registros es con el Asistente para aplicaciones. El Asistente para aplicaciones crea la clase de vista de registros y su clase de conjunto de registros asociada como parte de la aplicación de inicio esqueleto. Si no crea la clase de vista de registros con el Asistente para aplicaciones, puede crearla más adelante con ClassWizard. Si solo necesita un único formulario, el enfoque del Asistente para aplicaciones es más fácil. ClassWizard le permite decidir usar una vista de registros más adelante en el proceso de desarrollo. El uso de ClassWizard para crear una vista de registros y un conjunto de registros por separado y, a continuación, conectarlos es el enfoque más flexible, ya que ofrece un mayor control sobre el nombre de la clase de conjunto de registros y su. H/. Archivos CPP. Este enfoque también permite tener varias vistas de registros en la misma clase de conjunto de registros.

Para que los usuarios finales puedan moverse de un registro a otro en la vista de registros, el Asistente para aplicaciones crea recursos de menú (y, opcionalmente, barra de herramientas) para desplazarse al primer registro, siguiente, anterior o último. Si crea una clase de vista de registros con ClassWizard, debe crear estos recursos con el menú y los editores de mapas de bits.

Para obtener información sobre la implementación predeterminada para pasar de un registro a otro, consulte `IsOnFirstRecord` y `IsOnLastRecord` y el artículo [uso de una vista de registros](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView` realiza un seguimiento de la posición del usuario en el conjunto de registros para que la vista de registros pueda actualizar la interfaz de usuario. Cuando el usuario se mueve a cualquier extremo del conjunto de registros, la vista de registros deshabilita los objetos de interfaz de usuario, como los elementos de menú o los botones de la barra de herramientas, para moverse más en la misma dirección.

Para obtener más información sobre la declaración y el uso de las clases de conjunto de registros y vista de registros, vea "diseñar y crear una vista de registros" en el artículo [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener más información sobre cómo funcionan las vistas de registros y cómo usarlas, vea el artículo [uso de una vista de registros](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb. h

##  <a name="crecordview"></a>CRecordView:: CRecordView

Al crear un objeto de un tipo derivado de `CRecordView`, llame a cualquier forma del constructor para inicializar el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*nIDTemplate*<br/>
Contiene el número de identificador de un recurso de plantilla de cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Puede identificar el recurso por su nombre (pasar una cadena como argumento al constructor) o por su identificador (pasar un entero sin signo como argumento). Se recomienda usar un identificador de recurso.

> [!NOTE]
>  La clase derivada *debe* proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor `CRecordView::CRecordView` con el nombre o el identificador del recurso como argumento, tal como se muestra en el ejemplo siguiente.

`CRecordView::OnInitialUpdate` llama a `UpdateData`, que llama a `DoDataExchange`. Esta llamada inicial a `DoDataExchange` conecta `CRecordView` controles (indirectamente) con `CRecordset` miembros de datos de campo creados por ClassWizard. Estos miembros de datos no se pueden usar hasta que se llame a la clase base `CFormView::OnInitialUpdate` función miembro.

> [!NOTE]
>  Si usa ClassWizard, el asistente define un valor de **enumeración** `CRecordView::IDD`, lo especifica en la declaración de clase y lo utiliza en la lista de inicialización de miembros para el constructor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>CRecordView:: IsOnFirstRecord

Llame a esta función miembro para determinar si el registro actual es el primer registro del objeto de conjunto de registros asociado a esta vista de registros.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro actual es el primer registro del conjunto de registros; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función es útil para escribir sus propias implementaciones de controladores de actualización de comandos predeterminados escritos por ClassWizard.

Si el usuario se mueve al primer registro, el marco de trabajo deshabilita los objetos de interfaz de usuario que tenga para moverse al primer registro o al anterior.

##  <a name="isonlastrecord"></a>CRecordView:: IsOnLastRecord

Llame a esta función miembro para determinar si el registro actual es el último registro del objeto de conjunto de registros asociado a esta vista de registros.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro actual es el último registro del conjunto de registros; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función es útil para escribir sus propias implementaciones de los controladores de actualización de comandos predeterminados que ClassWizard escribe para admitir una interfaz de usuario para pasar de un registro a otro.

> [!CAUTION]
>  El resultado de esta función es confiable, con la diferencia de que la vista no puede detectar el final del conjunto de registros hasta que el usuario lo ha pasado. El usuario debe moverse más allá del último registro antes de que la vista de registros indique que debe deshabilitar los objetos de interfaz de usuario para moverse al siguiente registro o al último. Si el usuario se mueve más allá del último registro y, a continuación, se desplaza de nuevo al último registro (o antes), la vista de registros puede realizar un seguimiento de la posición del usuario en el conjunto de registros y deshabilitar correctamente los objetos de la interfaz de usuario. `IsOnLastRecord` también es poco confiable después de una llamada a la función de implementación `OnRecordLast`, que controla el comando de ID_RECORD_LAST o `CRecordset::MoveLast`.

##  <a name="ongetrecordset"></a>CRecordView:: OnGetRecordset

Devuelve un puntero al objeto derivado de `CRecordset`asociado a la vista de registros.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto derivado de `CRecordset`si el objeto se creó correctamente; de lo contrario, un puntero nulo.

### <a name="remarks"></a>Comentarios

Debe reemplazar esta función miembro para construir u obtener un objeto de conjunto de registros y devolver un puntero a él. Si declara la clase de vista de registros con ClassWizard, el asistente escribe una invalidación predeterminada. La implementación predeterminada de ClassWizard devuelve el puntero de conjunto de registros almacenado en la vista de registros si existe uno. De lo contrario, crea un objeto de conjunto de registros del tipo especificado con ClassWizard y llama a su función miembro `Open` para abrir la tabla o ejecutar la consulta y, a continuación, devuelve un puntero al objeto.

Para obtener más información y ejemplos, vea el artículo [vistas de registros: usar una vista de registros](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>CRecordView:: Move

Llame a esta función miembro para desplace a otro registro del conjunto de registros y muestre sus campos en los controles de la vista de registros.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parámetros

*nIDMoveCommand*<br/>
Uno de los siguientes valores de identificador de comando estándar:

- ID_RECORD_FIRST moverse al primer registro del conjunto de registros.

- ID_RECORD_LAST moverse al último registro del conjunto de registros.

- ID_RECORD_NEXT moverse al siguiente registro del conjunto de registros.

- ID_RECORD_PREV moverse al registro anterior del conjunto de registros.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el movimiento se realizó correctamente; de lo contrario, 0 si se denegó la solicitud de movimiento.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama a la función miembro `Move` adecuada del `CRecordset` objeto asociado a la vista de registros.

De forma predeterminada, `OnMove` actualiza el registro actual en el origen de datos si el usuario lo ha modificado en la vista de registros.

El Asistente para aplicaciones crea un recurso de menú con los elementos de menú primer registro, último registro, Registro siguiente y registro anterior. Si selecciona la opción de la barra de herramientas acoplable, el Asistente para aplicaciones también crea una barra de herramientas con botones correspondientes a estos comandos.

Si se mueve más allá del último registro del conjunto de registros, la vista de registros continúa mostrando el último registro. Si retrocede más allá del primer registro, la vista de registros continúa mostrando el primer registro.

> [!CAUTION]
>  La llamada a `OnMove` produce una excepción si el conjunto de registros no tiene registros. Llame a la función de controlador de actualización de la interfaz de usuario adecuada (`OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`o `OnUpdateRecordPrev`) antes de la operación de movimiento correspondiente para determinar si el conjunto de registros tiene registros.

## <a name="see-also"></a>Vea también

[CFormView (clase)](../../mfc/reference/cformview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)<br/>
[CFormView (clase)](../../mfc/reference/cformview-class.md)
