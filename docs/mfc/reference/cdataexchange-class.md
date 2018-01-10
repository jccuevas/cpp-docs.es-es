---
title: CDataExchange (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e56df3ec4604a02ba9cf1075152a11eefe7e28f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdataexchange-class"></a>CDataExchange (clase)
Admite rutinas de intercambio de datos de cuadros de diálogo (DDX) y de validación de datos de cuadros de diálogo (DDV) utilizadas por las clases de Microsoft Foundation.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDataExchange  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataExchange::CDataExchange](#cdataexchange)|Construye un objeto `CDataExchange`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataExchange::Fail](#fail)|Se llama cuando se produce un error de validación. Restablece el foco al control anterior e inicia una excepción.|  
|[CDataExchange::PrepareCtrl](#preparectrl)|Prepara el control especificado para el intercambio de datos o la validación. Se usa para controles de nonedit.|  
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Prepara el control de edición especificado para el intercambio de datos o la validación.|  
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Prepara el control OLE especificado para el intercambio de datos o la validación. Se usa para controles de nonedit.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Marca para la dirección de DDX y DDV.|  
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|El cuadro de diálogo o ventana donde el intercambio de datos tiene lugar.|  
  
## <a name="remarks"></a>Comentarios  
 `CDataExchange`no tiene una clase base.  
  
 Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos personalizados o controles, o si va a escribir sus propias rutinas de validación de datos. Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y [cuadros de diálogo](../../mfc/dialog-boxes.md).  
  
 Un `CDataExchange` objeto proporciona la información de contexto necesaria para colocan DDX y DDV tomar. La marca `m_bSaveAndValidate` es **FALSE** cuando DDX se usa para rellenar los valores iniciales de los controles de cuadro de diálogo de miembros de datos. La marca `m_bSaveAndValidate` es **TRUE** cuando DDX se usa para establecer los valores actuales de los controles de cuadro de diálogo en miembros de datos y el momento en que DDV se utiliza para validar los valores de datos. Si se produce un error en la validación de DDV, el procedimiento DDV mostrará un cuadro de mensaje que explica el error en la entrada. A continuación, se llamará al procedimiento DDV **producirá un error en** para restablecer el foco al control de proceso causante del error e inicia una excepción para detener el proceso de validación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CDataExchange`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cdataexchange"></a>CDataExchange::CDataExchange  
 Llame a esta función miembro para construir un `CDataExchange` objeto.  
  
```  
CDataExchange(
    CWnd* pDlgWnd,  
    BOOL bSaveAndValidate);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDlgWnd*  
 Un puntero a la ventana primaria que contiene el control. Normalmente esto es un [CDialog](../../mfc/reference/cdialog-class.md)-objeto derivado.  
  
 `bSaveAndValidate`  
 Si **TRUE**, este objeto se valida los datos, a continuación, escribe los datos de los controles a los miembros. Si **FALSE**, moverá este objeto datos de los miembros a los controles.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CDataExchange` objeto para almacenar información adicional en el objeto de intercambio de datos para pasar a la ventana [CWnd:: DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]  
  
##  <a name="fail"></a>CDataExchange::Fail  
 El marco de trabajo llama a esta función miembro cuando se produce un error en una operación de validación (DDV) de datos de cuadro de diálogo.  
  
```  
void Fail();
```  
  
### <a name="remarks"></a>Comentarios  
 **Un error** restaura el foco y la selección en el control cuya validación con errores (si hay un control para restaurar). **Un error** , a continuación, inicia una excepción de tipo [CUserException](../../mfc/reference/cuserexception-class.md) para detener el proceso de validación. La excepción hace que un cuadro de mensaje que explica que se muestre el error. Después de que se produce un error en la validación de DDV, el usuario puede volver a escribir datos en el control de proceso causante del error.  
  
 Pueden llamar los implementadores de rutinas DDV personalizadas **producirá un error en** de sus rutinas cuando se produce un error en la validación.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate  
 Esta marca indica la dirección de una operación de intercambio (DDX) de datos de cuadro de diálogo.  
  
```  
BOOL m_bSaveAndValidate;  
```  
  
### <a name="remarks"></a>Comentarios  
 La marca es distinto de cero si la `CDataExchange` objeto se usa para mover datos desde los controles de cuadro de diálogo a miembros de datos de la clase de cuadro de diálogo después de que el usuario edita los controles. La marca es cero si el objeto se utiliza para inicializar los controles de cuadro de diálogo de miembros de datos de la clase de cuadro de diálogo.  
  
 La marca también es distinto de cero durante la validación de datos de cuadro de diálogo (DDV).  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd  
 Contiene un puntero a la [CWnd](../../mfc/reference/cwnd-class.md) objeto para qué cuadro de diálogo (DDX) de intercambio de datos o la validación (DDV) se lleva a cabo.  
  
```  
CWnd* m_pDlgWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este objeto suele ser un [CDialog](../../mfc/reference/cdialog-class.md) objeto. Los implementadores de rutinas DDX o DDV personalizadas pueden utilizar este puntero para obtener acceso a la ventana de cuadro de diálogo que contiene los controles que funcionan en.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="preparectrl"></a>CDataExchange::PrepareCtrl  
 El marco de trabajo llama a esta función miembro para preparar el control especificado para el intercambio de datos de cuadros de diálogo (DDX) y la validación (DDV).  
  
```  
HWND PrepareCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDC`  
 El identificador del control para estar preparado para DDX o DDV.  
  
### <a name="return-value"></a>Valor devuelto  
 El `HWND` del control que se está preparando para DDX o DDV.  
  
### <a name="remarks"></a>Comentarios  
 Usar [PrepareEditCtrl](#prepareeditctrl) en su lugar para los controles de edición; use esta función miembro para todos los demás controles.  
  
 Preparación consta de almacenar el control `HWND` en la `CDataExchange` clase. El marco de trabajo usa este identificador para restaurar el foco en el control con el foco previamente si se produce un error DDX o DDV.  
  
 Deben llamar los implementadores de rutinas DDX o DDV personalizadas `PrepareCtrl` para todos los controles de edición distinta para el que se intercambian datos a través de DDX o validación de datos a través de DDV.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl  
 El marco de trabajo llama a esta función miembro para preparar el control de edición especificado para el intercambio de datos de cuadros de diálogo (DDX) y la validación (DDV).  
  
```  
HWND PrepareEditCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDC`  
 El identificador del control de edición para estar preparado para DDX o DDV.  
  
### <a name="return-value"></a>Valor devuelto  
 El `HWND` del control de edición que se está preparando para DDX o DDV.  
  
### <a name="remarks"></a>Comentarios  
 Use [PrepareCtrl](#preparectrl) en su lugar para todos los controles de edición no.  
  
 Preparación consta de dos cosas. En primer lugar, `PrepareEditCtrl` almacena el control `HWND` en la `CDataExchange` clase. El marco de trabajo usa este identificador para restaurar el foco en el control con el foco previamente si se produce un error DDX o DDV. Segundo, `PrepareEditCtrl` establece una marca el `CDataExchange` clase para indicar que el control de cuyos datos se intercambian o validado es un control de edición.  
  
 Deben llamar los implementadores de rutinas DDX o DDV personalizadas `PrepareEditCtrl` para todos los controles a los que se intercambian datos a través de DDX o validación de datos a través de DDV de edición.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
##  <a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl  
 El marco de trabajo llama a esta función miembro para preparar el control OLE especificado para el intercambio de datos de cuadros de diálogo (DDX) y la validación (DDV).  
  
```  
COleControlSite* PrepareOleCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDC`  
 El identificador del control OLE para estar preparado para DDX o DDV.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al sitio del control OLE.  
  
### <a name="remarks"></a>Comentarios  
 Use [PrepareEditCtrl](#prepareeditctrl) en su lugar para controles de edición o [PrepareCtrl](#preparectrl) para todos los demás controles no son compatibles con OLE.  
  
 Deben llamar los implementadores de rutinas DDX o DDV personalizadas `PrepareOleCtrl` para todos los controles OLE a los que se intercambian datos a través de DDX o validación de datos a través de DDV.  
  
 Para obtener más información sobre cómo escribir sus propias rutinas DDX y DDV, vea [Nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md). Para obtener información general de DDX y DDV, vea [intercambio de datos de cuadros de diálogo y validación](../../mfc/dialog-data-exchange-and-validation.md) y [temas del cuadro de diálogo](../../mfc/dialog-boxes.md).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo VIEWEX de MFC](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd:: DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)   
 [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)

