---
title: Clase COleDispatchException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
dev_langs: C++
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e25d83c2ae91424e80b07282bc5967a34745f412
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="coledispatchexception-class"></a>Clase COleDispatchException
Controla las excepciones específicas de la interfaz OLE de `IDispatch` , que es una parte fundamental de la automatización OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDispatchException : public CException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Contexto de ayuda para el error.|  
|[COleDispatchException::m_strDescription](#m_strdescription)|Descripción del error.|  
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Archivo de ayuda para usar con `m_dwHelpContext`.|  
|[COleDispatchException::m_strSource](#m_strsource)|Aplicación que generó la excepción.|  
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-código de error específico.|  
  
## <a name="remarks"></a>Comentarios  
 Como las demás clases de excepción que se derivan de la `CException` de la clase base `COleDispatchException` puede utilizarse con el **THROW**, `THROW_LAST`, **intente**, **CATCH**, `AND_CATCH`, y `END_CATCH` macros.  
  
 En general, debería llamar a [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) a crear e iniciar un `COleDispatchException` objeto.  
  
 Para obtener más información sobre excepciones, vea los artículos [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: excepciones OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext  
 Identifica un contexto de ayuda en la Ayuda de la aplicación (. Archivo HLP).  
  
```  
DWORD m_dwHelpContext;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleDispatchDriver:: CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_strdescription"></a>COleDispatchException::m_strDescription  
 Contiene una descripción del error, como "Disco lleno".  
  
```  
CString m_strDescription;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleDispatchDriver:: CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile  
 El marco de trabajo rellena esta cadena con el nombre del archivo de Ayuda de la aplicación.  
  
```  
CString m_strHelpFile;  
```  
  
##  <a name="m_strsource"></a>COleDispatchException::m_strSource  
 El marco de trabajo rellena esta cadena con el nombre de la aplicación que generó la excepción.  
  
```  
CString m_strSource;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleDispatchDriver:: CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_wcode"></a>COleDispatchException::m_wCode  
 Contiene un código de error que se refiere a la aplicación.  
  
```  
WORD m_wCode;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo CALCDRIV de MFC](../../visual-cpp-samples.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)   
 [COleException (clase)](../../mfc/reference/coleexception-class.md)
