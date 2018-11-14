---
title: COleDBRecordView (clase)
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
ms.openlocfilehash: fbbaaae72c7b58f898735d768c019a02cdb7d7e5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518585"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView (clase)

Una vista que muestra registros de una base de datos en controles.

## <a name="syntax"></a>Sintaxis

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Construye un objeto `COleDBRecordView`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Devuelve un valor HRESULT estándar.|
|[COleDBRecordView::OnMove](#onmove)|Actualiza el registro actual (si no guardados) en el origen de datos y, a continuación, se mueve al registro especificado (siguiente, anterior, primero o último).|

## <a name="remarks"></a>Comentarios

La vista es una vista de formulario conectada directamente a un `CRowset` objeto. La vista se crea a partir de un recurso de plantilla de cuadro de diálogo y muestra los campos de la `CRowset` objeto en los controles de la plantilla de cuadro de diálogo. El `COleDBRecordView` objeto utiliza el intercambio de datos de cuadro de diálogo (DDX) y la funcionalidad de exploración integrada en `CRowset`, para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de filas. `COleDBRecordView` También proporciona una implementación predeterminada para desplazarse al primero, siguiente, anterior o el último registro y una interfaz para actualizar el registro actualmente en la vista.

Puede utilizar funciones DDX con `COleDbRecordView` para obtener datos directamente desde el conjunto de registros de base de datos y mostrarlos en un control de cuadro de diálogo. Debe usar el `DDX_*` métodos (como `DDX_Text`), no el `DDX_Field*` funciones (como `DDX_FieldText`) con `COleDbRecordView`. `DDX_FieldText` no funcionará con `COleDbRecordView` porque `DDX_FieldText` toma un argumento adicional de tipo `CRecordset*` (para `CRecordView`) o `CDaoRecordset*` (para `CDaoRecordView`).

> [!NOTE]
>  Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de plantilla de consumidor OLE DB, utilice la clase [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) en su lugar. Para obtener más información, vea el artículo [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView` realiza un seguimiento de la posición del usuario en el conjunto de filas para que la vista de registros pueda actualizar la interfaz de usuario. Cuando el usuario se desplaza a cualquiera de los extremos del conjunto de filas, la vista de registros deshabilita los objetos de interfaz de usuario, como los elementos de menú o botones de barra de herramientas, para mover con más detalle en la misma dirección.

Para obtener más información acerca de las clases de conjunto de filas, vea el [utilizando OLE DB plantillas de consumidor](../../data/oledb/ole-db-consumer-templates-cpp.md) artículo.

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

##  <a name="coledbrecordview"></a>  COleDBRecordView::COleDBRecordView

Construye un objeto `COleDBRecordView`.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*nIDTemplate*<br/>
Contiene el número de Id. de un recurso de plantilla de cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Cuando se crea un objeto de un tipo derivado de `COleDBRecordView`, invocar uno de los constructores para crear el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista. Puede identificar el recurso por su nombre (pase una cadena como argumento al constructor) o por su identificador (pasar un entero sin signo como argumento).

> [!NOTE]
>  La clase derivada *debe* proporcionar su propio constructor. En el constructor, invocar el constructor, `COleDBRecordView::COleDBRecordView`, con el nombre del recurso o el identificador como argumento.

##  <a name="ongetrowset"></a>  COleDBRecordView::OnGetRowset

Devuelve un identificador para el **CRowset <>** objeto asociado a la vista de registros.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Debe reemplazar esta función miembro para construir u obtener un objeto de conjunto de filas y devolver un identificador a él. Si se declara la clase de vista de registros con ClassWizard, el asistente escribe un reemplazo predeterminado para usted. Implementación de predeterminada de ClassWizard devuelve el identificador de conjunto de filas almacenado en la vista de registro si existe alguno. Si no, construye un objeto de conjunto de filas del tipo especificado con ClassWizard y llama a su `Open` miembro funcione para abrir la tabla o ejecutar la consulta y, a continuación, devuelve un identificador al objeto.

> [!NOTE]
>  Anteriores a 7.0 de MFC, `OnGetRowset` devuelve un puntero a `CRowset`. Si tiene código que llama a `OnGetRowset`, deberá cambiar el tipo de valor devuelto a la clase de plantilla **<> CRowset**.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Para obtener más información y ejemplos, vea el artículo [vistas de registros: utilizar una vista de registros](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>  COleDBRecordView::OnMove

Se desplaza a un registro diferente en el conjunto de filas y mostrar sus campos en los controles del registro de ver.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parámetros

*nIDMoveCommand*<br/>
Uno de los siguientes valores de Id. de comando estándar:

- ID_RECORD_FIRST: Mover al primer registro en el conjunto de registros.

- ID_RECORD_LAST: Mover al último registro del conjunto de registros.

- ID_RECORD_NEXT: Mueva al siguiente registro del conjunto de registros.

- ID_RECORD_PREV: Mueva al registro anterior en el conjunto de registros.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el movimiento se realizó correctamente; en caso contrario, 0 si se denegó la solicitud de movimiento.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama adecuado `Move` función miembro de la `CRowset` objeto asociado a la vista de registros.

De forma predeterminada, `OnMove` actualiza el registro actual en el origen de datos si el usuario ha cambiado en la vista de registros.

El Asistente para aplicaciones crea un recurso de menú con los elementos de menú del primer registro, último registro, registro siguiente y registro anterior. Si selecciona la opción de barra de herramientas acoplable, el Asistente para la aplicación también crea una barra de herramientas con botones que corresponden a estos comandos.

Si mueve más allá del último registro del conjunto de registros, la vista de registros continúa mostrando el último registro. Si mueve más allá del primer registro hacia atrás, la vista de registros continúa mostrando el primer registro.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

