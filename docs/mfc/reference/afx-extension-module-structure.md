---
title: AFX_EXTENSION_MODULE (Estructura)
ms.date: 11/04/2016
f1_keywords:
- AFX_EXTENSION_MODULE
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
ms.openlocfilehash: e1bdc9d744424ab0ad59be3bd7b815b5122bcd10
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292840"
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

*bInitialized*<br/>
TRUE si se ha inicializado el módulo DLL con `AfxInitExtensionModule`.

*hModule*<br/>
Especifica el identificador del módulo DLL.

*hResource*<br/>
Especifica el identificador del módulo DLL de recurso personalizado.

*pFirstSharedClass*<br/>
Un puntero a la información (el `CRuntimeClass` estructura) acerca de la clase en tiempo de ejecución de la primera del módulo DLL. Se usa para proporcionar el inicio de la lista de clase en tiempo de ejecución.

*pFirstSharedFactory*<br/>
Un puntero al primer generador de objetos del módulo DLL (un `COleObjectFactory` objeto). Se usa para proporcionar el inicio de la lista de fábricas de clase.

## <a name="remarks"></a>Comentarios

Extensión MFC DLL necesario hacer dos cosas en sus `DllMain` función:

- Llame a [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) y compruebe el valor devuelto.

- Crear un `CDynLinkLibrary` objeto si va a exportar el archivo DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objetos o tiene sus propios recursos personalizados.

El `AFX_EXTENSION_MODULE` estructura se usa para mantener una copia de la extensión MFC estado del módulo DLL, incluida una copia de los objetos de clase en tiempo de ejecución que se hayan inicializado por el archivo DLL de extensión MFC como parte de la construcción del objeto estático normal ejecutada antes de `DllMain` es especificado. Por ejemplo:

[!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]

La información de módulo almacenada en el `AFX_EXTENSION_MODULE` estructura se puede copiar en el `CDynLinkLibrary` objeto. Por ejemplo:

[!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)<br/>
[AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)
