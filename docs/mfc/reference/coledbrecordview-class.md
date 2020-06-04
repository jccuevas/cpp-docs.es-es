---
title: Clase COleDBRecordView
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: de9c602cb747ee3d4449df479530e55ce907cb8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366103"
---
# <a name="coledbrecordview-class"></a>Clase COleDBRecordView

Una vista que muestra registros de una base de datos en controles.

## <a name="syntax"></a>Sintaxis

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Construye un objeto `COleDBRecordView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Devuelve un valor HRESULT estándar.|
|[COleDBRecordView::OnMove](#onmove)|Actualiza el registro actual (si está sucio) en el origen de datos y, a continuación, se mueve al registro especificado (siguiente, anterior, primero o último).|

## <a name="remarks"></a>Observaciones

La vista es una vista `CRowset` de formulario conectada directamente a un objeto. La vista se crea a partir de un `CRowset` recurso de plantilla de cuadro de diálogo y muestra los campos del objeto en los controles de la plantilla de cuadro de diálogo. El `COleDBRecordView` objeto utiliza el intercambio de datos de cuadro `CRowset`de diálogo (DDX) y la funcionalidad de navegación integrada en , para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de filas. `COleDBRecordView`también proporciona una implementación predeterminada para pasar al primer, siguiente, anterior o último registro y una interfaz para actualizar el registro actualmente en vista.

Puede utilizar funciones `COleDbRecordView` DDX con para obtener datos directamente del conjunto de registros de base de datos y mostrarlos en un control de cuadro de diálogo. Debe utilizar `DDX_*` los métodos `DDX_Text`(como `DDX_Field*` ), no `DDX_FieldText`las `COleDbRecordView`funciones (como ) con . `DDX_FieldText`no funcionará `COleDbRecordView` con `DDX_FieldText` porque toma un `CRecordset*` argumento `CRecordView`adicional `CDaoRecordset*` de `CDaoRecordView`tipo (para ) o (para ).

> [!NOTE]
> Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de plantilla de consumidor OLE DB, utilice la clase [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) en su lugar. Para obtener más información, consulte el artículo [Información general: Programación](../../data/data-access-programming-mfc-atl.md)de bases de datos .

`COleDBRecordView`realiza un seguimiento de la posición del usuario en el conjunto de filas para que la vista de registros pueda actualizar la interfaz de usuario. Cuando el usuario se mueve a cualquiera de los extremos del conjunto de filas, la vista de registros deshabilita los objetos de la interfaz de usuario, como los elementos de menú o los botones de la barra de herramientas, para avanzar en la misma dirección.

Para obtener más información acerca de las clases de conjunto de filas, consulte el uso de plantillas de [consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) artículo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxoledb.h

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView

Construye un objeto `COleDBRecordView`.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*nIDTemplate*<br/>
Contiene el número de identificador de un recurso de plantilla de cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Al crear un objeto de un `COleDBRecordView`tipo derivado de , invoque uno de los constructores para crear el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista. Puede identificar el recurso por nombre (pasar una cadena como argumento al constructor) o por su identificador (pasar un entero sin signo como argumento).

> [!NOTE]
> La clase derivada *debe* proporcionar su propio constructor. En el constructor, invoque el constructor, `COleDBRecordView::COleDBRecordView`, con el nombre de recurso o el identificador como argumento.

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a>COleDBRecordView::OnGetRowset

Devuelve un identificador para el **CRowset<>** objeto asociado a la vista de registros.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Debe invalidar esta función miembro para construir u obtener un objeto de conjunto de filas y devolverle un identificador. Si declara la clase de vista de registros con ClassWizard, el asistente escribe una invalidación predeterminada. La implementación predeterminada de ClassWizard devuelve el identificador de conjunto de filas almacenado en la vista de registros si existe uno. Si no es así, construye un objeto de conjunto de `Open` filas del tipo especificado con ClassWizard y llama a su función miembro para abrir la tabla o ejecutar la consulta y, a continuación, devuelve un identificador al objeto.

> [!NOTE]
> Antes de MFC 7.0, `OnGetRowset` `CRowset`devolvía un puntero a . Si tiene código `OnGetRowset`que llama a , debe cambiar el tipo de valor devuelto a la clase templatizada **CRowset<>**.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Para obtener más información y ejemplos, consulte el artículo Vistas de [registros: Uso](../../data/using-a-record-view-mfc-data-access.md)de una vista de registros .

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a>COleDBRecordView::OnMove

Se mueve a un registro diferente en el conjunto de filas y muestra sus campos en los controles de la vista de registro.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parámetros

*nIDMoveCommand*<br/>
Uno de los siguientes valores de ID de comando estándar:

- ID_RECORD_FIRST: vaya al primer registro del conjunto de registros.

- ID_RECORD_LAST: vaya al último registro del conjunto de registros.

- ID_RECORD_NEXT: vaya al siguiente registro del conjunto de registros.

- ID_RECORD_PREV: mover al registro anterior del conjunto de registros.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el movimiento se realizó correctamente; de lo contrario 0 si la solicitud de mudanza fue denegada.

### <a name="remarks"></a>Observaciones

La implementación predeterminada `Move` llama a `CRowset` la función miembro adecuada del objeto asociado a la vista de registros.

De forma `OnMove` predeterminada, actualiza el registro actual en el origen de datos si el usuario lo ha cambiado en la vista de registros.

El Asistente para aplicaciones crea un recurso de menú con los elementos de menú Primer registro, Ultimo registro, Siguiente registro y Registro anterior. Si selecciona la opción Barra de herramientas acoplable, el Asistente para aplicaciones también crea una barra de herramientas con botones correspondientes a estos comandos.

Si pasa el último registro del conjunto de registros, la vista de registros continúa mostrando el último registro. Si retrocede más allá del primer registro, la vista de registro continúa mostrando el primer registro.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
