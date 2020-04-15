---
title: CDaoRecordView (clase)
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: b8c411dbd29316219759351f1f1633b6e57b92e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377139"
---
# <a name="cdaorecordview-class"></a>CDaoRecordView (clase)

Una vista que muestra registros de una base de datos en controles.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoRecordView::CDaoRecordView](#cdaorecordview)|Construye un objeto `CDaoRecordView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Devuelve distinto de cero si el registro actual es el primer registro del conjunto de registros asociado.|
|[CDaoRecordView::IsonLastRecord](#isonlastrecord)|Devuelve distinto de cero si el registro actual es el último registro del conjunto de registros asociado.|
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Devuelve un puntero a un objeto `CDaoRecordset`de una clase derivada de . ClassWizard reemplaza esta función automáticamente y crea el conjunto de registros si es necesario.|
|[CDaoRecordView::OnMove](#onmove)|Si el registro actual ha cambiado, lo actualiza en el origen de datos y, a continuación, se mueve al registro especificado (siguiente, anterior, primero o último).|

## <a name="remarks"></a>Observaciones

La vista es una vista `CDaoRecordset` de formulario conectada directamente a un objeto. La vista se crea a partir de un `CDaoRecordset` recurso de plantilla de cuadro de diálogo y muestra los campos del objeto en los controles de la plantilla de cuadro de diálogo. El `CDaoRecordView` objeto utiliza el intercambio de datos de cuadro de diálogo (DDX) y el intercambio de campos de registros DAO (DFX) para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de registros. `CDaoRecordView`también proporciona una implementación predeterminada para pasar al primer, siguiente, anterior o último registro y una interfaz para actualizar el registro actualmente en vista.

> [!NOTE]
> Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO; las clases DAO generalmente ofrecen capacidades superiores porque utilizan el motor de base de datos Microsoft Jet.

La forma más común de crear la vista de registros es con el Asistente para aplicaciones. El Asistente para aplicaciones crea la clase de vista de registros y su clase de conjunto de registros asociada como parte de la aplicación de inicio de esqueleto.

Si simplemente necesita un único formulario, el enfoque del Asistente para aplicaciones es más fácil. ClassWizard le permite decidir usar una vista de registro más adelante en el proceso de desarrollo. Si no crea la clase de vista de registros con el Asistente para aplicaciones, puede crearla más adelante con ClassWizard. El uso de ClassWizard para crear una vista de registros y un conjunto de registros por separado y, a continuación, conectarlos es el enfoque más flexible porque proporciona más control en el nombre de la clase de conjunto de registros y su . H/. Archivos CPP. Este enfoque también le permite tener varias vistas de registros en la misma clase de conjunto de registros.

Para facilitar a los usuarios finales pasar de un registro a otro en la vista de registros, el Asistente para aplicaciones crea recursos de menú (y, opcionalmente, barra de herramientas) para pasar al primer, siguiente, anterior o último registro. Si crea una clase de vista de registros con ClassWizard, debe crear estos recursos usted mismo con los editores de menú y mapa de bits.

Para obtener información acerca de la implementación `IsOnFirstRecord` `IsOnLastRecord` predeterminada para pasar de un registro a `CDaoRecordView`otro, vea y el artículo Uso de una [vista](../../data/using-a-record-view-mfc-data-access.md)de registro , que se aplica a ambos `CRecordView` y .

`CDaoRecordView`realiza un seguimiento de la posición del usuario en el conjunto de registros para que la vista de registros pueda actualizar la interfaz de usuario. Cuando el usuario se mueve a cualquiera de los extremos del conjunto de registros, la vista de registros deshabilita los objetos de la interfaz de usuario, como los elementos de menú o los botones de la barra de herramientas, para avanzar en la misma dirección.

Para obtener más información sobre cómo declarar y usar la vista de registros y las clases de conjunto de registros, vea "Diseñar y crear una vista de registros" en el artículo [Vistas](../../data/record-views-mfc-data-access.md)de registros . Para obtener más información sobre cómo funcionan las vistas de registros y cómo usarlas, consulte el artículo Uso de [una vista](../../data/using-a-record-view-mfc-data-access.md)de registros . Todos los artículos mencionados anteriormente se aplican tanto a ambos `CRecordView` como `CDaoRecordView`a .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDaoRecordView::CDaoRecordView

Al crear un objeto de un `CDaoRecordView`tipo derivado de , llame a cualquiera de las formas del constructor para inicializar el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*nIDTemplate*<br/>
Contiene el número de identificador de un recurso de plantilla de cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Puede identificar el recurso por nombre (pasar una cadena como argumento al constructor) o por su identificador (pasar un entero sin signo como argumento). Se recomienda usar un identificador de recurso.

> [!NOTE]
> La clase derivada debe proporcionar su propio constructor. En el constructor de la clase `CDaoRecordView::CDaoRecordView` derivada, llame al constructor con el nombre de recurso o el identificador como argumento.

`CDaoRecordView::OnInitialUpdate`llamadas `CWnd::UpdateData`, `CWnd::DoDataExchange`que llama a . Esta llamada `DoDataExchange` inicial `CDaoRecordView` para conectar controles `CDaoRecordset` (indirectamente) a los miembros de datos de campo creados por ClassWizard. Estos miembros de datos no se `CFormView::OnInitialUpdate` pueden usar hasta después de llamar a la función miembro de clase base.

> [!NOTE]
> Si usa ClassWizard, el asistente define `CDaoRecordView::IDD` un valor **de enumeración** en la declaración de clase y lo utiliza en la lista de inicialización de miembro para el constructor.

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecordView::IsOnFirstRecord

Llame a esta función miembro para determinar si el registro actual es el primer registro en el objeto de conjunto de registros asociado a esta vista de registro.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro actual es el primer registro del conjunto de registros; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función es útil para escribir sus propias implementaciones de los controladores de actualización de comandos predeterminados escritos por ClassWizard.

Si el usuario se mueve al primer registro, el marco de trabajo deshabilita los objetos de interfaz de usuario (por ejemplo, elementos de menú o botones de barra de herramientas) que tiene para desplazarse al primer registro o al registro anterior.

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecordView::IsonLastRecord

Llame a esta función miembro para determinar si el registro actual es el último registro en el objeto de conjunto de registros asociado a esta vista de registro.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro actual es el último registro del conjunto de registros; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función es útil para escribir sus propias implementaciones de los controladores de actualización de comandos predeterminados que ClassWizard escribe para admitir una interfaz de usuario para pasar de un registro a otro.

> [!CAUTION]
> El resultado de esta función es confiable, excepto que es posible que la vista no pueda detectar el final del conjunto de registros hasta que el usuario se haya movido más allá de él. Es posible que el usuario tenga que ir más allá del último registro antes de que la vista de registros pueda indicar que debe deshabilitar los objetos de interfaz de usuario para pasar al registro siguiente o al último. Si el usuario pasa el último registro y, a continuación, vuelve al último registro (o antes de él), la vista de registros puede realizar un seguimiento de la posición del usuario en el conjunto de registros y deshabilitar los objetos de interfaz de usuario correctamente.

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView::OnGetRecordset

Devuelve un puntero `CDaoRecordset`al objeto derivado asociado a la vista de registros.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Valor devuelto

Puntero a `CDaoRecordset`un objeto derivado si el objeto se creó correctamente; de lo contrario, un puntero NULL.

### <a name="remarks"></a>Observaciones

Debe invalidar esta función miembro para construir u obtener un objeto de conjunto de registros y devolver un puntero a él. Si declara la clase de vista de registros con ClassWizard, el asistente escribe una invalidación predeterminada. La implementación predeterminada de ClassWizard devuelve el puntero de conjunto de registros almacenado en la vista de registros si existe uno. Si no es así, construye un objeto de conjunto de `Open` registros del tipo especificado con ClassWizard y llama a su función miembro para abrir la tabla o ejecutar la consulta y, a continuación, devuelve un puntero al objeto.

Para obtener más información y ejemplos, consulte el artículo Vistas de [registros: Uso](../../data/using-a-record-view-mfc-data-access.md)de una vista de registros .

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDaoRecordView::OnMove

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

La implementación predeterminada llama a `CDaoRecordset` la función miembro Move adecuada del objeto asociado a la vista de registros.

De forma `OnMove` predeterminada, actualiza el registro actual en el origen de datos si el usuario lo ha cambiado en la vista de registros.

El Asistente para aplicaciones crea un recurso de menú con los elementos de menú Primer registro, Ultimo registro, Siguiente registro y Registro anterior. Si selecciona la opción Barra de herramientas inicial, el Asistente para aplicaciones también crea una barra de herramientas con botones correspondientes a estos comandos.

Si pasa el último registro del conjunto de registros, la vista de registros continúa mostrando el último registro. Si retrocede más allá del primer registro, la vista de registro continúa mostrando el primer registro.

> [!CAUTION]
> Al `OnMove` llamar se produce una excepción si el conjunto de registros no tiene registros. Llame a la función `OnUpdateRecordFirst`de `OnUpdateRecordLast` `OnUpdateRecordNext`controlador `OnUpdateRecordPrev` de actualización de la interfaz de usuario adecuada (, , , , o) antes de la operación de movimiento correspondiente para determinar si el conjunto de registros tiene registros.

## <a name="see-also"></a>Consulte también

[Clase CFormView](../../mfc/reference/cformview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[Clase CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[Clase CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Clase CFormView](../../mfc/reference/cformview-class.md)
