---
title: CDaoRecordView (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- CDaoRecordView class
- data-bound controls [C++], DAO controls
- data binding [C++], DAO views
- bound controls [C++], displaying database data
- application wizards [C++], creating record views
- controls [MFC], data binding
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 11aa318e84e89835ceb710725590f3c3e6387fcd
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cdaorecordview-class"></a>CDaoRecordView (clase)
Una vista que muestra registros de una base de datos en controles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class AFX_NOVTABLE CDaoRecordView : public CFormView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoRecordView::CDaoRecordView](#cdaorecordview)|Construye un objeto `CDaoRecordView`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Devuelve cero si el registro actual es el primer registro en el conjunto de registros asociado.|  
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|Devuelve cero si el registro actual es el último registro en el conjunto de registros asociado.|  
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Devuelve un puntero a un objeto de una clase derivada de `CDaoRecordset`. ClassWizard reemplaza esta función automáticamente y crea el conjunto de registros si es necesario.|  
|[CDaoRecordView::OnMove](#onmove)|Si ha cambiado el registro actual, actualizaciones en el origen de datos, a continuación, se mueve al registro especificado (siguiente, anterior, primera o última).|  
  
## <a name="remarks"></a>Comentarios  
 La vista es una vista de formulario que se conecta directamente a un `CDaoRecordset` objeto. La vista se crea a partir de un recurso de plantilla de cuadro de diálogo y muestra los campos de la `CDaoRecordset` objeto en controles de la plantilla de cuadro de diálogo. La `CDaoRecordView` objeto utiliza el intercambio de datos de cuadro de diálogo (DDX) y de intercambio de campos de registros DAO (DFX) para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de registros. `CDaoRecordView`También proporciona una implementación predeterminada para desplazarse al primer, siguiente, anterior o último registro y una interfaz para actualizar el registro actual de la vista.  
  
> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Puede seguir acceso a orígenes de datos ODBC con las clases DAO; Generalmente, las clases DAO ofrecen capacidades de superior porque usan el motor de base de datos Microsoft Jet.  
  
 Es la manera más común para crear la vista de registros con el Asistente para aplicaciones. El Asistente para aplicaciones crea la clase de vista de registros y su clase de conjunto de registros asociado como parte de la aplicación esqueleto starter.  
  
 Si simplemente necesita un único formulario, el enfoque del Asistente para aplicaciones es más fácil. ClassWizard permite decidir utilizar una vista de registros más adelante en el proceso de desarrollo. Si no se crea la clase de vista de registros con el Asistente para aplicaciones, puede crearla posteriormente con ClassWizard. Uso de ClassWizard para crear una vista de registros y un conjunto de registros por separado y, después, conéctelas es el enfoque más flexible porque le ofrece más control en la clase de conjunto de registros de nombres y su. H /. Archivos CPP. Este enfoque permite tener varias vistas de registros en la misma clase de conjunto de registros.  
  
 Para facilitar a los usuarios finales para desplazarse por los registros en la vista de registros, el Asistente para aplicaciones crea la barra de menús (y opcionalmente) para mover los recursos al primero, siguiente, anterior o el último registro. Si crea una clase de vista de registros con el asistente, debe crear estos recursos usted mismo con el menú y el mapa de bits editores.  
  
 Para obtener información acerca de la implementación predeterminada para desplazarse por los registros, consulte `IsOnFirstRecord` y `IsOnLastRecord` y el artículo [mediante una vista de registros](../../data/using-a-record-view-mfc-data-access.md), que se aplica a ambos `CRecordView` y `CDaoRecordView`.  
  
 `CDaoRecordView`realiza un seguimiento de la posición del usuario en el conjunto de registros para que la vista de registro pueda actualizar la interfaz de usuario. Cuando el usuario se desplaza a cualquier extremo del conjunto de registros, la vista del registro deshabilita los objetos de la interfaz de usuario, como elementos de menú o botones de barra de herramientas, para mover más en la misma dirección.  
  
 Para obtener más información acerca de cómo declarar y utilizar la vista de registros y las clases de conjunto de registros, vea "Diseñar y crear una vista de registro" en el artículo [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener más información acerca de cómo ve el registro de trabajo y cómo usarlas, vea el artículo [mediante una vista de registros](../../data/using-a-record-view-mfc-data-access.md). Todos los artículos mencionados anteriormente se aplican a ambos `CRecordView` y `CDaoRecordView`.  
  
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
  
##  <a name="cdaorecordview"></a>CDaoRecordView::CDaoRecordView  
 Cuando se crea un objeto de un tipo derivado de `CDaoRecordView`, llame a cualquiera de las formas del constructor para inicializar el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista.  
  
```  
explicit CDaoRecordView(LPCTSTR lpszTemplateName);  
explicit CDaoRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTemplateName`  
 Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.  
  
 `nIDTemplate`  
 Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 O bien, puede identificar el recurso por nombre (pase una cadena como argumento al constructor) o por su identificador (pasar un entero sin signo como argumento). Id. se recomienda usar un recurso.  
  
> [!NOTE]
>  La clase derivada debe proporcionar su propio constructor. En el constructor de la clase derivada, llame al constructor de `CDaoRecordView::CDaoRecordView` con el nombre del recurso o el identificador como argumento.  
  
 **CDaoRecordView::OnInitialUpdate** llamadas `CWnd::UpdateData`, que llama `CWnd::DoDataExchange`. Esta llamada inicial a `DoDataExchange` conecta `CDaoRecordView` (indirectamente) con controles `CDaoRecordset` creados por el Asistente para clases de miembros de datos de campo. No se puede usar estos miembros de datos hasta después de llamar a la clase base **CFormView::OnInitialUpdate** función miembro.  
  
> [!NOTE]
>  Si utiliza el asistente, el asistente define un `enum` valor `CDaoRecordView::IDD` en la declaración de clase y los usa en la inicialización del miembro de lista para el constructor.  
  
 [!code-cpp[NVC_MFCDatabase&#35;](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>CDaoRecordView::IsOnFirstRecord  
 Llame a esta función miembro para determinar si el registro actual es el primer registro en el objeto de conjunto de registros asociado a esta vista de registro.  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el registro actual es el primer registro del conjunto de registros; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es útil para escribir sus propias implementaciones de forma predeterminada, la controladores de actualización de comandos escritos ClassWizard.  
  
 Si el usuario se mueve al primer registro, el deshabilita framework objetos de interfaz de usuario (por ejemplo, elementos de menú o botones de barra de herramientas) tiene para moverse a la primera o en el registro anterior.  
  
##  <a name="isonlastrecord"></a>CDaoRecordView::IsOnLastRecord  
 Llame a esta función miembro para determinar si el registro actual es el último registro en el objeto de conjunto de registros asociado a esta vista de registro.  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el registro actual es el último registro del conjunto de registros; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es útil para escribir sus propias implementaciones de forma predeterminada, la controladores de actualización de comandos que escribe ClassWizard para admitir una interfaz de usuario para desplazarse por los registros.  
  
> [!CAUTION]
>  El resultado de esta función es confiable, salvo que la vista no pueda detectar el final del conjunto de registros hasta que el usuario se desplazó péguela. El usuario tendría que mover más allá del último registro antes de la vista de registros puede indicar que deben deshabilitar los objetos de la interfaz de usuario para desplazarse al siguiente o al último registro. Si el usuario se mueve más allá del último registro y, a continuación, desplaza al último registro (o anterior), la vista de registros puede realizar un seguimiento de la posición del usuario en el conjunto de registros y deshabilitar correctamente los objetos de la interfaz de usuario.  
  
##  <a name="ongetrecordset"></a>CDaoRecordView::OnGetRecordset  
 Devuelve un puntero a la `CDaoRecordset`-derivadas objeto asociado a la vista de registros.  
  
```  
virtual CDaoRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CDaoRecordset`-objeto derivado, si el objeto se creó correctamente; en caso contrario, un **NULL** puntero.  
  
### <a name="remarks"></a>Comentarios  
 Debe reemplazar esta función miembro para construir u obtenga un objeto recordset y devolver un puntero a él. Si se declara la clase de vista de registros con ClassWizard, el asistente escribe una invalidación de forma predeterminada. Implementación predeterminada de ClassWizard devuelve el puntero de conjunto de registros almacenado en la vista de registros, si existe. Si no, construye un objeto de conjunto de registros del tipo especificado con ClassWizard y llama a su **abrir** miembro de función para abrir la tabla o ejecutar la consulta y, a continuación, devuelve un puntero al objeto.  
  
 Para obtener más información y ejemplos, vea el artículo [vistas de registros: utilizar una vista de registros](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>CDaoRecordView::OnMove  
 Llame a esta función miembro para moverse a un registro diferente del conjunto de registros y mostrar sus campos en los controles de la vista de registros.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDMoveCommand`  
 Uno de los valores de Id. de comando estándar siguientes:  
  
- `ID_RECORD_FIRST`Mover al primer registro del conjunto de registros.  
  
- `ID_RECORD_LAST`Mover al último registro del conjunto de registros.  
  
- `ID_RECORD_NEXT`Mover al siguiente registro del conjunto de registros.  
  
- `ID_RECORD_PREV`Mover al registro anterior del conjunto de registros.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el desplazamiento se realiza correctamente; en caso contrario, 0 si se denegó la solicitud de movimiento.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama a la función de miembro adecuada de movimiento de la `CDaoRecordset` objeto asociado a la vista de registros.  
  
 De forma predeterminada, `OnMove` actualiza el registro actual en el origen de datos si el usuario ha cambiado en la vista de registros.  
  
 El Asistente para aplicaciones crea un recurso de menú con elementos de menú del primer registro, último registro, registro siguiente y registro anterior. Si selecciona la opción de la barra de herramientas inicial, el Asistente para aplicaciones también crea una barra de herramientas con botones que corresponden a estos comandos.  
  
 Si se pasa más allá del último registro del conjunto de registros, la vista de registros continúa mostrando el último registro. Si se mueve hacia atrás más allá del primer registro, la vista de registros continuará mostrando el primer registro.  
  
> [!CAUTION]
>  Llamar a `OnMove` produce una excepción si el objeto recordset no tiene registros. Llame a la función de controlador de actualización de interfaz de usuario correspondiente: **OnUpdateRecordFirst**, **OnUpdateRecordLast**, **OnUpdateRecordNext**, o **OnUpdateRecordPrev** : correspondiente antes de mover la operación para determinar si el conjunto de registros tiene todos los registros.  
  
## <a name="see-also"></a>Vea también  
 [Clase CFormView](../../mfc/reference/cformview-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)   
 [Clase CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace (clase)](../../mfc/reference/cdaoworkspace-class.md)   
 [Clase CFormView](../../mfc/reference/cformview-class.md)

