---
title: COleDBRecordView (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- MFC, OLE DB
- COleDBRecordView class
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 6129ad49f58cecb099927fe3d422fe215d143b67
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Devuelve un estándar `HRESULT` valor.|  
|[COleDBRecordView::OnMove](#onmove)|Actualiza el registro actual (si se ha cambiado) en el origen de datos y, a continuación, se mueve al registro especificado (siguiente, anterior, primera o última).|  
  
## <a name="remarks"></a>Comentarios  
 La vista es una vista de formulario directamente conectada a un `CRowset` objeto. La vista se crea a partir de un recurso de plantilla de cuadro de diálogo y muestra los campos de la `CRowset` objeto en los controles de la plantilla de cuadro de diálogo. El `COleDBRecordView` objeto utiliza el intercambio de datos de cuadros de diálogo (DDX) y la funcionalidad de exploración integrada en `CRowset`, para automatizar el movimiento de datos entre los controles en el formulario y los campos del conjunto de filas. `COleDBRecordView`También proporciona una implementación predeterminada para desplazarse a la primera, siguiente, anterior o el último registro y una interfaz para actualizar el registro actualmente en la vista.  
  
 Puede utilizar funciones DDX con **COleDbRecordView** para obtener datos directamente desde el conjunto de registros de base de datos y mostrarlos en un control de cuadro de diálogo. Debe utilizar el **DDX_\*** métodos (como `DDX_Text`), no el **DDX_Field\* ** funciones (como `DDX_FieldText`) con **COleDbRecordView**. `DDX_FieldText`no funcionará con **COleDbRecordView** porque `DDX_FieldText` toma un argumento adicional de tipo **CRecordset\*** (para `CRecordView`) o **CDaoRecordset\* ** (para `CDaoRecordView`).  
  
> [!NOTE]
>  Si está trabajando con las clases de Data Access Objects (DAO) en lugar de las clases de plantilla de consumidor OLE DB, utilice la clase [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) en su lugar. Para obtener más información, vea el artículo [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 `COleDBRecordView`realiza un seguimiento de la posición del usuario en el conjunto de filas para que la vista de registros pueda actualizar la interfaz de usuario. Cuando el usuario se desplaza a cualquiera de los extremos del conjunto de filas, la vista de registros deshabilita objetos de la interfaz de usuario, como botones de barra de herramientas o elementos de menú, para mover más en la misma dirección.  
  
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
  
##  <a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView  
 Construye un objeto `COleDBRecordView`.  
  
```  
COleDBRecordView(LPCTSTR lpszTemplateName);  
COleDBRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTemplateName`  
 Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.  
  
 `nIDTemplate`  
 Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto de un tipo derivado de `COleDBRecordView`, invocar uno de los constructores para crear el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista. Puede identificar el recurso por su nombre (pasa una cadena como argumento al constructor) o por su identificador (pase un entero sin signo como argumento).  
  
> [!NOTE]
>  La clase derivada *debe* proporcionar su propio constructor. En el constructor, invocar el constructor, `COleDBRecordView::COleDBRecordView`, con el nombre del recurso o el identificador como un argumento.  
  
##  <a name="ongetrowset"></a>COleDBRecordView::OnGetRowset  
 Devuelve un identificador para el **CRowset<> </>** objeto asociado a la vista de registros.  
  
```  
virtual CRowset<>* OnGetRowset() = 0;  
 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Se debe reemplazar esta función miembro para construir u obtenga un objeto de conjunto de filas y devolver un identificador a él. Si se declara la clase de vista de registros con ClassWizard, el asistente escribe una invalidación de forma predeterminada para usted. Implementación de predeterminada de ClassWizard devuelve el identificador de conjunto de filas almacenado en la vista de registros, si existe uno. Si no es así, construye un objeto de conjunto de filas del tipo especificado con ClassWizard y llama a su **abrir** miembro de función para abrir la tabla o ejecutar la consulta y, a continuación, devuelve un identificador al objeto.  
  
> [!NOTE]
>  Anterior a la versión MFC 7.0, `OnGetRowset` devuelve un puntero a `CRowset`. Si tiene código que llama a `OnGetRowset`, debe cambiar el tipo de valor devuelto a la clase con plantillas **CRowset<>**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase #38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]  
  
 Para obtener más información y ejemplos, vea el artículo [vistas de registros: utilizar una vista de registros](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>COleDBRecordView::OnMove  
 Se desplaza a un registro diferente en el conjunto de filas y mostrar sus campos en los controles del registro ver.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDMoveCommand`  
 Uno de los siguientes valores de Id. de comando estándar:  
  
- `ID_RECORD_FIRST`Migre al primer registro del conjunto de registros.  
  
- `ID_RECORD_LAST`Mueva hasta el último registro en el conjunto de registros.  
  
- `ID_RECORD_NEXT`Mueva hasta el siguiente registro del conjunto de registros.  
  
- `ID_RECORD_PREV`Migre al registro anterior en el conjunto de registros.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el movimiento se realizó correctamente; en caso contrario es 0 si se denegó la solicitud de movimiento.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama adecuado **mover** función miembro de la `CRowset` objeto asociado a la vista de registros.  
  
 De forma predeterminada, `OnMove` actualiza el registro actual en el origen de datos si el usuario ha cambiado en la vista de registros.  
  
 El Asistente para aplicaciones crea un recurso de menú con elementos de menú del primer registro, último registro, registro siguiente y registro anterior. Si selecciona la opción de barra de herramientas acoplable, el Asistente para aplicaciones también crea una barra de herramientas con botones que corresponden a estos comandos.  
  
 Si mueve más allá del último registro en el conjunto de registros, la vista de registros continúa mostrando el último registro. Si se mueve hacia atrás más allá del primer registro, la vista de registros continúa mostrando el primer registro.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)




