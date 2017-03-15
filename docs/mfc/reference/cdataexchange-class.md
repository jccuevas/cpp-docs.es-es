---
title: CDataExchange (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataExchange
dev_langs:
- C++
helpviewer_keywords:
- DDX/DDV, Technical Note 26
- DDX/DDV, CDataExchange class
- DDX (dialog data exchange), direction of exchange
- DDX (dialog data exchange), between dialog and CDialog
- DDX (dialog data exchange), custom DDX routines
- DDV (dialog data validation)
- m_bSaveAndValidate
- CDataExchange class
- exchanging data between dialogs and CDialogs
- DDV (dialog data validation), custom DDV routines
- DDX/DDV
- DDX (dialog data exchange)
- validating data, dialog box data entry
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 8f35e87d562a894411401755ccd4fdd54e43b58a
ms.lasthandoff: 02/24/2017

---
# <a name="cdataexchange-class"></a>CDataExchange (clase)
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
|[CDataExchange::Fail](#fail)|Se llama cuando se produce un error de validación. Restablece el foco al control anterior y produce una excepción.|  
|[CDataExchange::PrepareCtrl](#preparectrl)|Prepara el control especificado para el intercambio de datos o validación. Uso de controles de nonedit.|  
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Prepara el control de edición especificado para el intercambio de datos o validación.|  
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Prepara el control OLE especificado para el intercambio de datos o la validación. Uso de controles de nonedit.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Marca la dirección de DDX y DDV.|  
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|El cuadro de diálogo o ventana donde los datos de exchange tiene lugar.|  
  
## <a name="remarks"></a>Comentarios  
 `CDataExchange`no tiene una clase base.  
  
 Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos personalizados o controles, o si va a escribir sus propias rutinas de validación de datos. Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md) y [cuadros de diálogo](../../mfc/dialog-boxes.md).  
  
 Un `CDataExchange` objeto proporciona la información de contexto necesaria para colocan DDX y DDV tomar. El indicador `m_bSaveAndValidate` es **FALSE** cuando DDX se utiliza para rellenar los valores iniciales de los controles de cuadro de diálogo de miembros de datos. El indicador `m_bSaveAndValidate` es **TRUE** cuando DDX se utiliza para establecer los valores actuales de los controles de cuadro de diálogo en miembros de datos y cuando DDV se utiliza para validar los valores de datos. Si falla la validación DDV, el procedimiento DDV mostrará un cuadro de mensaje que explica el error de entrada. A continuación, se llamará al procedimiento DDV **producirá un error** para restablecer el foco al control infractor e inicia una excepción para detener el proceso de validación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CDataExchange`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecdataexchangea--cdataexchangecdataexchange"></a><a name="cdataexchange"></a>CDataExchange::CDataExchange  
 Llame a esta función miembro para construir un `CDataExchange` objeto.  
  
```  
CDataExchange(
    CWnd* pDlgWnd,  
    BOOL bSaveAndValidate);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDlgWnd*  
 Puntero a la ventana primaria que contiene el control. Esta suele ser un [CDialog](../../mfc/reference/cdialog-class.md)-objeto derivado.  
  
 `bSaveAndValidate`  
 Si **TRUE**, este objeto se valida los datos, a continuación, escribe los datos de los controles a los miembros. Si **FALSE**, este objeto mueva datos de los miembros a los controles.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CDataExchange` objeto para almacenar información adicional en el objeto de intercambio de datos para pasar a la ventana [CWnd:: DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog&#70;](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]  
  
##  <a name="a-namefaila--cdataexchangefail"></a><a name="fail"></a>CDataExchange::Fail  
 El marco de trabajo llama a esta función miembro cuando se produce un error en una operación de validación (DDV) de datos de cuadro de diálogo.  
  
```  
void Fail();
```  
  
### <a name="remarks"></a>Comentarios  
 **Un error** restaura el foco y la selección en el control cuya validación de error (si hay un control para restaurar). **Un error** , a continuación, se produce una excepción de tipo [CUserException](../../mfc/reference/cuserexception-class.md) para detener el proceso de validación. La excepción hace que explica el error que se mostrará un cuadro de mensaje. Después de que se produce un error en la validación de DDV, el usuario puede volver a escribir datos en el control incorrecto.  
  
 Pueden llamar los implementadores de rutinas DDV **errores** desde sus rutinas cuando falla una validación.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="a-namembsaveandvalidatea--cdataexchangembsaveandvalidate"></a><a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate  
 Esta marca indica la dirección de una operación de intercambio de datos de cuadro de diálogo.  
  
```  
BOOL m_bSaveAndValidate;  
```  
  
### <a name="remarks"></a>Comentarios  
 El indicador es distinto de cero si la `CDataExchange` objeto es que se usa para mover datos desde los controles de cuadro de diálogo a miembros de datos de la clase de cuadro de diálogo después de que el usuario edite los controles. El indicador es cero si el objeto se utiliza para inicializar los controles de cuadro de diálogo de miembros de datos de la clase de cuadro de diálogo.  
  
 La marca también es distinto de cero durante la validación de datos de cuadro de diálogo (DDV).  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="a-namempdlgwnda--cdataexchangempdlgwnd"></a><a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd  
 Contiene un puntero a la [CWnd](../../mfc/reference/cwnd-class.md) objeto para el cuadro de diálogo (DDX) de intercambio de datos o la validación (DDV) se lleva a cabo.  
  
```  
CWnd* m_pDlgWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este objeto es normalmente un [CDialog](../../mfc/reference/cdialog-class.md) objeto. Los implementadores de rutinas DDX o DDV personalizadas pueden utilizar este puntero para obtener acceso a la ventana de cuadro de diálogo que contiene los controles que funcionan en.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="a-namepreparectrla--cdataexchangepreparectrl"></a><a name="preparectrl"></a>CDataExchange::PrepareCtrl  
 El marco de trabajo llama a esta función miembro para preparar el control especificado para el intercambio de datos de cuadro de diálogo (DDX) y la validación (DDV).  
  
```  
HWND PrepareCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDC`  
 El identificador del control para estar preparados para DDX y DDV.  
  
### <a name="return-value"></a>Valor devuelto  
 El `HWND` del control están preparado para DDX y DDV.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [PrepareEditCtrl](#prepareeditctrl) controles de edición; usar esta función miembro para todos los demás controles.  
  
 Preparación consta de almacenar el control `HWND` en la `CDataExchange` clase. El marco de trabajo utiliza este identificador para restaurar el foco en el control con foco anteriormente en caso de error DDX o DDV.  
  
 Deben llamar los implementadores de rutinas DDX o DDV `PrepareCtrl` para todos los controles de edición no para el que se intercambian datos a través de DDX o validación de datos a través de DDV.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="a-nameprepareeditctrla--cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl  
 El marco de trabajo llama a esta función miembro para preparar el control de edición especificado para el intercambio de datos de cuadro de diálogo (DDX) y la validación (DDV).  
  
```  
HWND PrepareEditCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDC`  
 El identificador del control de edición para estar preparados para DDX y DDV.  
  
### <a name="return-value"></a>Valor devuelto  
 El `HWND` del control de edición están preparado para DDX y DDV.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [PrepareCtrl](#preparectrl) en su lugar para todos los controles de edición no.  
  
 Preparación consta de dos cosas. Primero, `PrepareEditCtrl` almacena el control `HWND` en la `CDataExchange` clase. El marco de trabajo utiliza este identificador para restaurar el foco en el control con foco anteriormente en caso de error DDX o DDV. Segundo, `PrepareEditCtrl` establece una marca el `CDataExchange` clase para indicar que el control de cuyos datos se intercambian o validado es un control de edición.  
  
 Deben llamar los implementadores de rutinas DDX o DDV `PrepareEditCtrl` para todos los controles que se intercambian datos a través de DDX o validación de datos a través de DDV de edición.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="a-nameprepareolectrla--cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl  
 El marco de trabajo llama a esta función miembro para preparar el control OLE especificado para el intercambio de datos de cuadro de diálogo (DDX) y la validación (DDV).  
  
```  
COleControlSite* PrepareOleCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDC`  
 El identificador del control OLE para estar preparados para DDX y DDV.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al sitio del control OLE.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [PrepareEditCtrl](#prepareeditctrl) en su lugar para controles de edición o [PrepareCtrl](#preparectrl) para todos los demás controles no OLE.  
  
 Deben llamar los implementadores de rutinas DDX o DDV `PrepareOleCtrl` para todos los controles OLE que se intercambian datos a través de DDX o validación de datos a través de DDV.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [diálogo intercambio y validación de](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC VIEWEX](../../visual-cpp-samples.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWnd:: DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)   
 [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)


