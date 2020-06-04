---
title: COleLinkingDoc (clase)
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: 1fad986b7e7304075cacb0b5ced9feeb8af4664f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753840"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc (clase)

La clase base para documentos contenedores de OLE que admiten la vinculación a los elementos incrustados que contienen.

## <a name="syntax"></a>Sintaxis

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|Construye un objeto `COleLinkingDoc`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleLinkingDoc::Registro](#register)|Registra el documento con los archivos DLL del sistema OLE.|
|[COleLinkingDoc::Revocar](#revoke)|Revoca el registro del documento.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Busca el elemento incrustado especificado.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Busca el elemento vinculado especificado.|

## <a name="remarks"></a>Observaciones

Una aplicación contenedora que admite la vinculación a elementos incrustados se denomina "contenedor de vínculos." La aplicación de ejemplo [OCLIENT](../../overview/visual-cpp-samples.md) es un ejemplo de un contenedor de vínculos.

Cuando el origen de un elemento vinculado es un elemento incrustado en otro documento, ese documento que contiene debe cargarse para que se edite el elemento incrustado. Por este motivo, otra aplicación contenedora debe poder iniciar un contenedor de vínculos cuando el usuario desee editar el origen de un elemento vinculado. La aplicación también debe usar la [clase COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) para que pueda crear documentos cuando se inicie mediante programación.

Para convertir el contenedor en un contenedor `COleLinkingDoc` de vínculos, derive la clase de documento en lugar de [COleDocument](../../mfc/reference/coledocument-class.md). Al igual que con cualquier otro contenedor OLE, debe diseñar la clase para almacenar los datos nativos de la aplicación, así como los elementos incrustados o vinculados. Además, debe diseñar estructuras de datos para almacenar los datos nativos. Si define `CDocItem`una clase derivada para los datos nativos de la `COleDocument` aplicación, puede usar la interfaz definida para almacenar los datos nativos, así como los datos OLE.

Para permitir que la aplicación se inicie mediante `COleTemplateServer` programación mediante otro contenedor, `CWinApp`declare un objeto como miembro de la clase derivada de la aplicación:

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

En `InitInstance` la función `CWinApp`miembro de la clase derivada, `COleLinkingDoc`cree una plantilla de documento y especifique la clase derivada como la clase de documento:

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Conecte `COleTemplateServer` el objeto a las plantillas de `ConnectTemplate` documento llamando a la función miembro `COleTemplateServer::RegisterAll`del objeto y registre todos los objetos de clase con el sistema OLE llamando a:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Para obtener `CWinApp`una definición `InitInstance` y función de clase derivada de ejemplo, consulte OCLIENT. H y OCLIENT. CPP en el ejemplo [MFC OCLIENT](../../overview/visual-cpp-samples.md).

Para obtener más `COleLinkingDoc`información sobre el uso , vea los artículos [Contenedores: implementación](../../mfc/containers-implementing-a-container.md) de un contenedor y [contenedores: características avanzadas](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a>COleLinkingDoc::COleLinkingDoc

Construye un `COleLinkingDoc` objeto sin iniciar las comunicaciones con los archivos DLL del sistema OLE.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Observaciones

Debe llamar `Register` a la función miembro para informar a OLE de que el documento está abierto.

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a>COleLinkingDoc::OnFindEmbeddedItem

Llamado por el marco de trabajo para determinar si el documento contiene un elemento OLE incrustado con el nombre especificado.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parámetros

*lpszItemName*<br/>
Puntero al nombre del elemento OLE incrustado solicitado.

### <a name="return-value"></a>Valor devuelto

Un puntero al elemento especificado; NULL si no se encuentra el elemento.

### <a name="remarks"></a>Observaciones

La implementación predeterminada busca en la lista de elementos incrustados un elemento con el nombre especificado (la comparación de nombres distingue mayúsculas de minúsculas). Invalide esta función si tiene su propio método de almacenamiento o nomenclatura de elementos OLE incrustados.

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a>COleLinkingDoc::OnGetLinkedItem

Llamado por el marco de trabajo para comprobar si el documento contiene un elemento de servidor vinculado con el nombre especificado.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parámetros

*lpszItemName*<br/>
Puntero al nombre del elemento OLE vinculado solicitado.

### <a name="return-value"></a>Valor devuelto

Un puntero al elemento especificado; NULL si no se encuentra el elemento.

### <a name="remarks"></a>Observaciones

La `COleLinkingDoc` implementación predeterminada siempre devuelve NULL. Esta función se reemplaza en `COleServerDoc` la clase derivada para buscar en la lista de elementos de servidor OLE un elemento vinculado con el nombre especificado (la comparación de nombres distingue mayúsculas de minúsculas). Invalide esta función si ha implementado su propio método de almacenamiento o recuperación de elementos de servidor vinculados.

## <a name="colelinkingdocregister"></a><a name="register"></a>COleLinkingDoc::Registro

Informa a los archivos DLL del sistema OLE que el documento está abierto.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*pFactory*<br/>
Puntero a un objeto de fábrica OLE (puede ser NULL).

*lpszPathName*<br/>
Puntero a la ruta de acceso completa del documento contenedor.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se registra correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta función al crear o abrir un archivo con nombre para registrar el documento con los archivos DLL del sistema OLE. No es necesario llamar a esta función si el documento representa un elemento incrustado.

Si está `COleTemplateServer` utilizando en `Register` la aplicación, `COleLinkingDoc`se llama `OnNewDocument` `OnOpenDocument`por `OnSaveDocument`la implementación de , , y .

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a>COleLinkingDoc::Revocar

Informa a los archivos DLL del sistema OLE que el documento ya no está abierto.

```cpp
void Revoke();
```

### <a name="remarks"></a>Observaciones

Llame a esta función para revocar el registro del documento con los archivos DLL del sistema OLE.

Debe llamar a esta función al cerrar un archivo con nombre, pero normalmente no es necesario llamarlo directamente. `Revoke`es llamado por `COleLinkingDoc`la implementación `OnNewDocument` `OnOpenDocument`de `OnCloseDocument` `OnSaveDocument`, , , y .

## <a name="see-also"></a>Vea también

[Ejemplo de MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument (Clase)](../../mfc/reference/coledocument-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)
