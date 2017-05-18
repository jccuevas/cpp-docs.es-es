---
title: AFX_EXTENSION_MODULE (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
caps.latest.revision: 11
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
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: 4bc0dafbc4d09f5c53ff502876da2e250d537882
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE (Estructura)
El `AFX_EXTENSION_MODULE` se utiliza durante la inicialización de DLL de extensión MFC para almacenar el estado del módulo de archivo DLL de extensión.  
  
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
 **TRUE** si se ha inicializado el módulo DLL con `AfxInitExtensionModule`.  
  
 `hModule`  
 Especifica el identificador del módulo DLL.  
  
 *hResource*  
 Especifica el identificador del módulo de recursos personalizados de DLL.  
  
 *pFirstSharedClass*  
 Un puntero a la información (el `CRuntimeClass` estructura) acerca de la clase en tiempo de ejecución de la primera del módulo de archivo DLL. Se usa para proporcionar el inicio de la lista de clases en tiempo de ejecución.  
  
 *pFirstSharedFactory*  
 Un puntero al primer generador de objetos del módulo DLL (un `COleObjectFactory` objeto). Se usa para proporcionar el inicio de la lista del generador de clases.  
  
## <a name="remarks"></a>Comentarios  
 Extensión de MFC DLL necesario hacer dos cosas en sus `DllMain` función:  
  
-   Llame a [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) y compruebe el valor devuelto.  
  
-   Crear un **CDynLinkLibrary** si va a exportar el archivo DLL del objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objetos o tiene sus propios recursos personalizados.  
  
 El `AFX_EXTENSION_MODULE` estructura se utiliza para almacenar una copia de la extensión de estado de módulo DLL, incluida una copia de los objetos de clase en tiempo de ejecución que se ha inicializado por el archivo DLL de extensión como parte de la construcción del objeto estático normal ejecutada antes de `DllMain` se escribe. Por ejemplo:  
  
 [!code-cpp[NVC_MFC_DLL N.º 2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 La información de módulo almacenada en el `AFX_EXTENSION_MODULE` estructura puede copiarse en el **CDynLinkLibrary** objeto. Por ejemplo:  
  
 [!code-cpp[NVC_MFC_DLL Nº 5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)   
 [AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)


