---
title: CRecordView (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3784bfd637c40f326a67807d0002fae66177ac37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
|[CRecordView::CRecordView](#crecordview)|Construye un objeto `CRecordView`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Devuelve un valor distinto de cero si el registro actual es el primer registro en el conjunto de registros asociado.|  
|[CRecordView::IsOnLastRecord](#isonlastrecord)|Devuelve un valor distinto de cero si el registro actual es el último registro en el conjunto de registros asociado.|  
|[CRecordView::OnGetRecordset](#ongetrecordset)|Devuelve un puntero a un objeto de una clase derivada de `CRecordset`. ClassWizard reemplaza esta función automáticamente y crea el conjunto de registros si es necesario.|  
|[CRecordView::OnMove](#onmove)||  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordView::OnMove](#onmove)|Si ha cambiado el registro actual, se actualiza en el origen de datos, a continuación, se mueve al registro especificado (siguiente, anterior, primera o última).|  
  
## <a name="remarks"></a>Comentarios  
 La vista es una vista de formulario directamente conectada a un `CRecordset` objeto. La vista se crea a partir de un recurso de plantilla de cuadro de diálogo y muestra los campos de la `CRecordset` objeto en los controles de la plantilla de cuadro de diálogo. La `CRecordView` objeto utiliza intercambio de datos de cuadros de diálogo (DDX) y de intercambio de campos de registros (RFX) para automatizar el movimiento de datos entre los controles en el formulario y los campos del conjunto de registros. `CRecordView` También proporciona una implementación predeterminada para desplazarse a la primera, siguiente, anterior o el último registro y una interfaz para actualizar el registro actualmente en la vista.  
  
> [!NOTE]
>  Si está trabajando con las clases de Data Access Objects (DAO) en lugar de las clases de Open Database Connectivity (ODBC), utilice la clase [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) en su lugar. Para obtener más información, vea el artículo [información general: programación de base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Es la manera más común para crear la vista de registros con el Asistente para aplicaciones. Asistente para aplicaciones de GET crea la clase de vista de registros y su clase de conjunto de registros asociado como parte de la aplicación esqueleto starter. Si no crea la clase de vista de registros con el Asistente para aplicaciones, puede crearla posteriormente con ClassWizard. Si simplemente necesita un único formulario, el enfoque de Asistente para aplicaciones es más fácil. ClassWizard le permite decidir utilizar una vista de registros más adelante en el proceso de desarrollo. Uso de ClassWizard para crear una vista de registros y un conjunto de registros por separado y, después, conéctelas es el enfoque más flexible porque ofrece mayor control en el nombre de la clase de conjunto de registros y su. H /. Archivos CPP. Este enfoque también le permite tener varias vistas de registros en la misma clase de conjunto de registros.  
  
 Para facilitar a los usuarios finales para desplazarse por los registros en la vista de registros, el Asistente para aplicaciones crea la barra de menús (y opcionalmente) recursos para mover a la primera, siguiente, anterior o el último registro. Si crea una clase de vista de registros con ClassWizard, debe crear estos recursos usted mismo con el menú y el mapa de bits de editores.  
  
 Para obtener información acerca de la implementación predeterminada para desplazarse por los registros, vea `IsOnFirstRecord` y `IsOnLastRecord` y el artículo [mediante una vista de registros](../../data/using-a-record-view-mfc-data-access.md).  
  
 `CRecordView` realiza un seguimiento de la posición del usuario en el conjunto de registros para que la vista de registros pueda actualizar la interfaz de usuario. Cuando el usuario se desplaza a cualquiera de los extremos del conjunto de registros, la vista de registros deshabilita objetos de la interfaz de usuario, como botones de barra de herramientas o elementos de menú, para mover más en la misma dirección.  
  
 Para obtener más información sobre cómo declarar y usar la vista de registros y las clases de conjunto de registros, vea "Diseñar y crear una vista de registro" en el artículo [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener más información acerca de cómo registro presenta el trabajo y cómo usarlas, vea el artículo [mediante una vista de registros](../../data/using-a-record-view-mfc-data-access.md).  
  
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
  
##  <a name="crecordview"></a>  CRecordView::CRecordView  
 Cuando se crea un objeto de un tipo derivado de `CRecordView`, llamar a cualquiera de las formas del constructor para inicializar el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista.  
  
```  
explicit CRecordView(LPCTSTR lpszTemplateName);  
explicit CRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTemplateName`  
 Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.  
  
 `nIDTemplate`  
 Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 O bien puede identificar el recurso por su nombre (pasa una cadena como argumento al constructor) o por su identificador (pase un entero sin signo como argumento). Id. se recomienda usar un recurso.  
  
> [!NOTE]
>  La clase derivada *debe* proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor de `CRecordView::CRecordView` con el nombre del recurso o el identificador como argumento, como se muestra en el ejemplo siguiente.  
  
 **CRecordView::OnInitialUpdate** llamadas `UpdateData`, que llama `DoDataExchange`. Esta llamada inicial a `DoDataExchange` conecta `CRecordView` controla (indirectamente) con `CRecordset` campo los miembros de datos creados por ClassWizard. No se puede usar estos miembros de datos hasta después de llamar a la clase base **CFormView::OnInitialUpdate** función miembro.  
  
> [!NOTE]
>  Si usas ClassWizard, el asistente define un `enum` valor `CRecordView::IDD`, especifica en la declaración de clase y lo utiliza en la lista de inicialización de miembros para el constructor.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord  
 Llame a esta función miembro para determinar si el registro actual es el primer registro en el objeto de conjunto de registros asociado a esta vista de registros.  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el registro actual es el primer registro en el conjunto de registros; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es útil para escribir sus propias implementaciones de forma predeterminada de controladores de actualización de comandos escritos ClassWizard.  
  
 Si el usuario se mueve al primer registro, el marco de trabajo deshabilita los objetos de la interfaz de usuario que tiene para moverse a la primera o en el registro anterior.  
  
##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord  
 Llame a esta función miembro para determinar si el registro actual es el último registro en el objeto de conjunto de registros asociado a esta vista de registros.  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el registro actual es el último registro en el conjunto de registros; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es útil para escribir sus propias implementaciones de manera predeterminada en los controladores de actualización de comandos que escribe ClassWizard para admitir una interfaz de usuario para moverse entre los registros.  
  
> [!CAUTION]
>  El resultado de esta función es confiable, salvo que la vista no puede detectar el final del conjunto de registros hasta que el usuario se desplazó más allá de él. El usuario debe mover más allá del último registro antes de la vista de registros puede indicar que deben deshabilitar los objetos de interfaz de usuario para moverse a la siguiente o el último registro. Si el usuario mueve más allá del último registro y, a continuación, desplaza hasta el último registro (o antes de él), la vista de registros puede realizar un seguimiento de la posición del usuario en el conjunto de registros y deshabilitar correctamente los objetos de la interfaz de usuario. `IsOnLastRecord` También es confiable después de llamar a la función de la implementación **OnRecordLast**, que controla el `ID_RECORD_LAST` comando, o `CRecordset::MoveLast`.  
  
##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset  
 Devuelve un puntero a la `CRecordset`-derivadas objeto asociado a la vista de registros.  
  
```  
virtual CRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CRecordset`-objeto derivado si el objeto se creó correctamente; en caso contrario un **NULL** puntero.  
  
### <a name="remarks"></a>Comentarios  
 Se debe reemplazar esta función miembro para construir u obtenga un objeto de conjunto de registros y devolver un puntero a ella. Si se declara la clase de vista de registros con ClassWizard, el asistente escribe una invalidación de forma predeterminada para usted. Implementación de predeterminada de ClassWizard devuelve el puntero de conjunto de registros almacenado en la vista de registros, si existe uno. Si no es así, construye un objeto de conjunto de registros del tipo especificado con ClassWizard y llama a su **abrir** miembro de función para abrir la tabla o ejecutar la consulta y, a continuación, devuelve un puntero al objeto.  
  
 Para obtener más información y ejemplos, vea el artículo [vistas de registros: utilizar una vista de registros](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>  CRecordView::OnMove  
 Llame a esta función miembro para moverse a un registro diferente del conjunto de registros y mostrar sus campos en los controles de la vista de registros.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDMoveCommand`  
 Uno de los siguientes valores de Id. de comando estándar:  
  
- `ID_RECORD_FIRST` Mover al primer registro del conjunto de registros.  
  
- `ID_RECORD_LAST` Mover hasta el último registro en el conjunto de registros.  
  
- `ID_RECORD_NEXT` Mover hasta el siguiente registro del conjunto de registros.  
  
- `ID_RECORD_PREV` Mover al registro anterior en el conjunto de registros.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el movimiento se realizó correctamente; en caso contrario es 0 si se denegó la solicitud de movimiento.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama adecuado **mover** función miembro de la `CRecordset` objeto asociado a la vista de registros.  
  
 De forma predeterminada, `OnMove` actualiza el registro actual en el origen de datos si el usuario ha cambiado en la vista de registros.  
  
 El Asistente para aplicaciones crea un recurso de menú con elementos de menú del primer registro, último registro, registro siguiente y registro anterior. Si selecciona la opción de barra de herramientas acoplable, el Asistente para aplicaciones también crea una barra de herramientas con botones que corresponden a estos comandos.  
  
 Si mueve más allá del último registro en el conjunto de registros, la vista de registros continúa mostrando el último registro. Si se mueve hacia atrás más allá del primer registro, la vista de registros continúa mostrando el primer registro.  
  
> [!CAUTION]
>  Al llamar a `OnMove` produce una excepción si el conjunto de registros no tiene registros. Llame a la función de controlador de actualización de interfaz de usuario correspondiente: **OnUpdateRecordFirst**, **OnUpdateRecordLast**, **OnUpdateRecordNext**, o  **OnUpdateRecordPrev** : antes de la correspondiente operación de movimiento para determinar si el conjunto de registros tiene los registros.  
  
## <a name="see-also"></a>Vea también  
 [Clase CFormView](../../mfc/reference/cformview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)   
 [CFormView (clase)](../../mfc/reference/cformview-class.md)
