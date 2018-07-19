---
title: AFX_EXTENSION_MODULE (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65f1f2a6416ef93395f7ec73b27a89bf44e2d885
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339389"
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE (Estructura)
El `AFX_EXTENSION_MODULE` se usa durante la inicialización de DLL de extensión MFC para mantener el estado del módulo DLL de extensión MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct AFX_EXTENSION_MODULE  
{  
    BOOL bInitialized;  
    HMODULE hModule;  
    HMODULE hResource;  
    CRuntimeClass* pFirstSharedClass;  
    COleObjectFactory* pFirstSharedFactory;  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 *bInitialized*  
 TRUE si se ha inicializado el módulo DLL con `AfxInitExtensionModule`.  
  
 *hModule*  
 Especifica el identificador del módulo DLL.  
  
 *hResource*  
 Especifica el identificador del módulo DLL de recurso personalizado.  
  
 *pFirstSharedClass*  
 Un puntero a la información (el `CRuntimeClass` estructura) acerca de la clase en tiempo de ejecución de la primera del módulo DLL. Se usa para proporcionar el inicio de la lista de clase en tiempo de ejecución.  
  
 *pFirstSharedFactory*  
 Un puntero al primer generador de objetos del módulo DLL (un `COleObjectFactory` objeto). Se usa para proporcionar el inicio de la lista de fábricas de clase.  
  
## <a name="remarks"></a>Comentarios  
 Extensión MFC DLL necesario hacer dos cosas en sus `DllMain` función:  
  
-   Llame a [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) y compruebe el valor devuelto.  
  
-   Crear un `CDynLinkLibrary` objeto si va a exportar el archivo DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objetos o tiene sus propios recursos personalizados.  
  
 El `AFX_EXTENSION_MODULE` estructura se usa para mantener una copia de la extensión MFC estado del módulo DLL, incluida una copia de los objetos de clase en tiempo de ejecución que se hayan inicializado por el archivo DLL de extensión MFC como parte de la construcción del objeto estático normal ejecutada antes de `DllMain` es especificado. Por ejemplo:  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 La información de módulo almacenada en el `AFX_EXTENSION_MODULE` estructura se puede copiar en el `CDynLinkLibrary` objeto. Por ejemplo:  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)   
 [AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)

