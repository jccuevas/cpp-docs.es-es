---
title: Clase COleException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleException
dev_langs:
- C++
helpviewer_keywords:
- COleException class
- exceptions, OLE
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
caps.latest.revision: 22
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 059c92c8dc8796cf103cc02533ba5f3526720249
ms.lasthandoff: 02/24/2017

---
# <a name="coleexception-class"></a>Clase COleException
Representa una condición de excepción relacionada con una operación OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleException : public CException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleException::Process](#process)|Convierte una excepción detectada en un código de retorno de OLE.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleException::m_sc](#m_sc)|Contiene el código de estado que indica el motivo de la excepción.|  
  
## <a name="remarks"></a>Comentarios  
 La `COleException` clase incluye un miembro de datos público que contiene el código de estado que indica el motivo de la excepción.  
  
 En general, no debería crear un `COleException` objeto directamente; en su lugar, debe llamar a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).  
  
 Para obtener más información sobre las excepciones, consulte los artículos [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: excepciones OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="a-namemsca--coleexceptionmsc"></a><a name="m_sc"></a>COleException::m_sc  
 Este miembro de datos contiene el código de estado OLE que indica el motivo de la excepción.  
  
```  
SCODE m_sc;  
```  
  
### <a name="remarks"></a>Comentarios  
 Valor de la variable se establece [AfxThrowOleException](exception-processing.md#afxthrowoleexception).  
  
 Para obtener más información sobre `SCODE`, consulte [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#22;](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]  
  
##  <a name="a-nameprocessa--coleexceptionprocess"></a><a name="process"></a>COleException::Process  
 Llame a la **proceso** función miembro para traducir una excepción detectada en un código de estado OLE.  
  
```  
static SCODE PASCAL Process(const CException* pAnyException);
```  
  
### <a name="parameters"></a>Parámetros  
 *pAnyException*  
 Puntero a una excepción detectada.  
  
### <a name="return-value"></a>Valor devuelto  
 Un código de estado OLE.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Esta función es **estático**.  
  
 Para obtener más información sobre `SCODE`, consulte [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo CALCDRIV de MFC](../../visual-cpp-samples.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




