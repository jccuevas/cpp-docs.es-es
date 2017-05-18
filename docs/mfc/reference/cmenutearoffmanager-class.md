---
title: Clase CMenuTearOffManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
dev_langs:
- C++
helpviewer_keywords:
- CMenuTearOffManager class
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
caps.latest.revision: 31
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
ms.openlocfilehash: 53677bbea54e428e5f080f5c1f73c576abcf99a5
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmenutearoffmanager-class"></a>Clase CMenuTearOffManager
Administra menús con barra desplazable. Un menú con barra desplazable es un menú de la barra de menús. El usuario puede quitar un menú con barra desplazable de la barra de menús y provocar que el menú con barra desplazable quede flotante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMenuTearOffManager : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|Construye un objeto `CMenuTearOffManager`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMenuTearOffManager::Build](#build)||  
|[CMenuTearOffManager::GetRegPath](#getregpath)||  
|[CMenuTearOffManager::Initialize](#initialize)|Inicializa un `CMenuTearOffManager` objeto.|  
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||  
|[CMenuTearOffManager::Parse](#parse)||  
|[CMenuTearOffManager::Reset](#reset)||  
|[CMenuTearOffManager::SetInUse](#setinuse)||  
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||  
  
## <a name="remarks"></a>Comentarios  
 Para poder utilizar menús desplazable en su aplicación, debe tener un `CMenuTearOffManager` objeto. En la mayoría de los casos, no crear o inicializar un `CMenuTearOffManager` objeto directamente. Esto se realiza automáticamente cuando se llama a la [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) (función).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear e inicializar un `CMenuTearOffManager` objeto mediante una llamada a la `CWinAppEX::EnableTearOffMenus` (método). Este fragmento de código forma parte de la [ejemplo de panel de palabras](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad&#12;](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenuTearOffManager`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmenutearoffmanager.h  
  
##  <a name="build"></a>CMenuTearOffManager::Build  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Build(
    UINT uiTearOffBarID,  
    CString& strText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiTearOffBarID`  
 [in] `strText`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="cmenutearoffmanager"></a>CMenuTearOffManager::CMenuTearOffManager  
 Construye un [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objeto.  
  
```  
CMenuTearOffManager();
```  
  
### <a name="remarks"></a>Comentarios  
 En la mayoría de los casos, no debería crear un `CMenuTearOffManager` manualmente. El marco de trabajo de la aplicación crea el `CMenuTearOffManager` objeto cuando se llama a [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).  
  
##  <a name="getregpath"></a>CMenuTearOffManager::GetRegPath  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
LPCTSTR GetRegPath() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="initialize"></a>CMenuTearOffManager::Initialize  
 Inicializa un [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objeto.  
  
```  
BOOL Initialize(
    LPCTSTR lpszRegEntry,  
    UINT uiTearOffMenuFirst,  
    UINT uiTearOffMenuLast);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszRegEntry`  
 Cadena que contiene la ruta de acceso de una entrada del registro. Las aplicaciones se almacena la configuración de barras desplazable en esta entrada del registro.  
  
 [in] `uiTearOffMenuFirst`  
 El primer identificador de menú para un menú.  
  
 [in] `uiTearOffMenuLast`  
 El identificador del último menú para un menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El intervalo de identificadores de menú `uiTearOffMenuFirst` para `uiTearOffMenuLast` debe ser un intervalo continuo. El intervalo define el número de menús desplazable que pueden aparecer al mismo tiempo en la aplicación.  
  
##  <a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDynamicID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="parse"></a>CMenuTearOffManager::Parse  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
UINT Parse(CString& str);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `str`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="reset"></a>CMenuTearOffManager::Reset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Reset(HMENU hmenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hmenu`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setinuse"></a>CMenuTearOffManager::SetInUse  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetInUse(
    UINT uiCmdId,  
    BOOL bUse = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdId`  
 [in] `bUse`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetupTearOffMenus(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hMenu`  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)

