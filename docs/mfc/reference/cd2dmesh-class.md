---
title: Clase CD2DMesh | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
dev_langs:
- C++
helpviewer_keywords:
- CD2DMesh class
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
caps.latest.revision: 17
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
ms.openlocfilehash: 78461adeaa0671b146ccb48f4e9145cbdceeb8cf
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dmesh-class"></a>Clase CD2DMesh
Un contenedor para ID2D1Mesh.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DMesh : public CD2DResource;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Construye un objeto CD2DMesh.|  
|[CD2DMesh:: ~ CD2DMesh](#_dtorcd2dmesh)|Destructor. Se llama cuando se destruye un objeto de malla D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DMesh::Attach](#attach)|Conexiones existentes de la interfaz de recursos para el objeto|  
|[CD2DMesh::Create](#create)|Crea un CD2DMesh. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DMesh::Destroy](#destroy)|Destruye un objeto CD2DMesh. (Invalida [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DMesh::Detach](#detach)|Separa la interfaz de recursos desde el objeto|  
|[CD2DMesh::Get](#get)|Interfaz de ID2D1Mesh devuelve|  
|[CD2DMesh::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DMesh::Open](#open)|Se abre la malla de población.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DMesh::operator ID2D1Mesh *](#operator_id2d1mesh_star)|Interfaz de ID2D1Mesh devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DMesh::m_pMesh](#m_pmesh)|Puntero a un ID2D1Mesh.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DMesh`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcd2dmesh"></a>CD2DMesh:: ~ CD2DMesh  
 Destructor. Se llama cuando se destruye un objeto de malla D2D.  
  
```  
virtual ~CD2DMesh();
```  
  
##  <a name="attach"></a>CD2DMesh::Attach  
 Conexiones existentes de la interfaz de recursos para el objeto  
  
```  
void Attach(ID2D1Mesh* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="cd2dmesh"></a>CD2DMesh::CD2DMesh  
 Construye un objeto CD2DMesh.  
  
```  
CD2DMesh(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="create"></a>CD2DMesh::Create  
 Crea un CD2DMesh.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="destroy"></a>CD2DMesh::Destroy  
 Destruye un objeto CD2DMesh.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DMesh::Detach  
 Separa la interfaz de recursos desde el objeto  
  
```  
ID2D1Mesh* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz desasociadas recursos.  
  
##  <a name="get"></a>CD2DMesh::Get  
 Interfaz de ID2D1Mesh devuelve  
  
```  
ID2D1Mesh* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1Mesh o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="isvalid"></a>CD2DMesh::IsValid  
 Comprobaciones de validez de los recursos  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el recurso es válido; de lo contrario, FALSE.  
  
##  <a name="m_pmesh"></a>CD2DMesh::m_pMesh  
 Puntero a un ID2D1Mesh.  
  
```  
ID2D1Mesh* m_pMesh;  
```  
  
##  <a name="open"></a>CD2DMesh::Open  
 Se abre la malla de población.  
  
```  
ID2D1TessellationSink* Open();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un ID2D1TessellationSink que se usa para rellenar la malla.  
  
##  <a name="operator_id2d1mesh_star"></a>CD2DMesh::operator ID2D1Mesh *  
 Interfaz de ID2D1Mesh devuelve  
  
```  
operator ID2D1Mesh*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1Mesh o NULL si el objeto no se ha inicializado todavía.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

