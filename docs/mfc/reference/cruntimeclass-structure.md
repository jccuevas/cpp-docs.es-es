---
title: CRuntimeClass (estructura)
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: 92979a10c18d9759e0ecc9f0785e56a97c0f0642
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426790"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass (estructura)

Cada clase derivada de `CObject` está asociada a una estructura de `CRuntimeClass` que se puede utilizar para obtener información sobre un objeto o su clase base en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
struct CRuntimeClass
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRuntimeClass:: CreateObject](#createobject)|Crea un objeto en tiempo de ejecución.|
|[CRuntimeClass:: FromName](#fromname)|Crea un objeto durante el tiempo de ejecución utilizando el conocido nombre de clase.|
|[CRuntimeClass:: IsDerivedFrom](#isderivedfrom)|Determina si la clase se deriva de la clase especificada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRuntimeClass:: m_lpszClassName](#m_lpszclassname)|Nombre de la clase.|
|[CRuntimeClass:: m_nObjectSize](#m_nobjectsize)|Tamaño del objeto en bytes.|
|[CRuntimeClass:: m_pBaseClass](#m_pbaseclass)|Puntero a la estructura de `CRuntimeClass` de la clase base.|
|[CRuntimeClass:: m_pfnCreateObject](#m_pfncreateobject)|Puntero a la función que crea dinámicamente el objeto.|
|[CRuntimeClass:: m_pfnGetBaseClass](#m_pfngetbaseclass)|Devuelve la estructura de `CRuntimeClass` (solo disponible cuando se vincula dinámicamente).|
|[CRuntimeClass:: m_wSchema](#m_wschema)|El número de esquema de la clase.|

## <a name="remarks"></a>Observaciones

`CRuntimeClass` es una estructura y, por tanto, no tiene una clase base.

La capacidad de determinar la clase de un objeto en tiempo de ejecución es útil cuando se necesita comprobación de tipos adicional de argumentos de función o cuando se debe escribir código de propósito especial basado en la clase de un objeto. El lenguaje no admite directamente la C++ información de clase en tiempo de ejecución.

`CRuntimeClass` proporciona información sobre el objeto C++ relacionado, como un puntero al `CRuntimeClass` de la clase base y el nombre de clase ASCII de la clase relacionada. Esta estructura también implementa varias funciones que se pueden usar para crear objetos dinámicamente, especificando el tipo de objeto utilizando un nombre conocido y determinando si la clase relacionada se deriva de una clase específica.

Para obtener más información sobre el uso de `CRuntimeClass`, vea el artículo [acceso a la información de clase en tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CRuntimeClass`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="createobject"></a>CRuntimeClass:: CreateObject

Llame a esta función para crear dinámicamente la clase especificada en tiempo de ejecución.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
Nombre conocido de la clase que se va a crear.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto que se acaba de crear o NULL si no se encuentra el nombre de la clase o si no hay suficiente memoria para crear el objeto.

### <a name="remarks"></a>Observaciones

Las clases derivadas de `CObject` pueden admitir la creación dinámica, que es la capacidad de crear un objeto de una clase especificada en tiempo de ejecución. Por ejemplo, las clases de documento, vista y marco deben admitir la creación dinámica. Para obtener más información sobre la creación dinámica y el miembro `CreateObject`, vea [clase CObject](../../mfc/using-cobject.md) y [clase CObject: especificar niveles de funcionalidad](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="fromname"></a>CRuntimeClass:: FromName

Llame a esta función para recuperar la estructura de `CRuntimeClass` asociada al nombre conocido.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
Nombre conocido de una clase derivada de `CObject`.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto de `CRuntimeClass`, que se corresponde con el nombre que se pasa en *lpszClassName*. La función devuelve NULL si no se encuentra ningún nombre de clase coincidente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>CRuntimeClass:: IsDerivedFrom

Llame a esta función para determinar si la clase de llamada se deriva de la clase especificada en el parámetro *pBaseClass* .

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Parámetros

*pBaseClass*<br/>
Nombre conocido de una clase derivada de `CObject`.

### <a name="return-value"></a>Valor devuelto

TRUE si la clase que llama a `IsDerivedFrom` se deriva de la clase base cuya estructura de `CRuntimeClass` se proporciona como parámetro; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

La relación se determina mediante "caminar" desde la clase del miembro hacia arriba en la cadena de clases derivadas hasta la parte superior. Esta función solo devuelve FALSE si no se encuentra ninguna coincidencia para la clase base.

> [!NOTE]
>  Para utilizar la estructura `CRuntimeClass`, debe incluir la macro IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE o IMPLEMENT_SERIAL en la implementación de la clase para la que desea recuperar la información del objeto en tiempo de ejecución.

Para obtener más información sobre el uso de `CRuntimeClass`, vea el artículo [clase CObject: acceso a la información de clase en tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>CRuntimeClass:: m_lpszClassName

Una cadena terminada en null que contiene el nombre de clase ASCII.

### <a name="remarks"></a>Observaciones

Este nombre se puede utilizar para crear una instancia de la clase utilizando la función miembro `FromName`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_nobjectsize"></a>CRuntimeClass:: m_nObjectSize

Tamaño del objeto, en bytes.

### <a name="remarks"></a>Observaciones

Si el objeto tiene miembros de datos que apuntan a la memoria asignada, no se incluye el tamaño de esa memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pbaseclass"></a>CRuntimeClass:: m_pBaseClass

Si la aplicación se vincula estáticamente a MFC, este miembro de datos contiene un puntero a la estructura `CRuntimeClass` de la clase base.

### <a name="remarks"></a>Observaciones

Si la aplicación se vincula dinámicamente a la biblioteca MFC, vea [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pfncreateobject"></a>CRuntimeClass:: m_pfnCreateObject

Un puntero de función al constructor predeterminado que crea un objeto de la clase.

### <a name="remarks"></a>Observaciones

Este puntero solo es válido si la clase admite la creación dinámica; de lo contrario, la función devuelve NULL.

##  <a name="m_pfngetbaseclass"></a>CRuntimeClass:: m_pfnGetBaseClass

Si la aplicación utiliza la biblioteca MFC como un archivo DLL compartido, este miembro de datos señala a una función que devuelve la estructura `CRuntimeClass` de la clase base.

### <a name="remarks"></a>Observaciones

Si la aplicación se vincula estáticamente a la biblioteca MFC, vea [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_wschema"></a>CRuntimeClass:: m_wSchema

El número de esquema (-1 para clases no serializables).

### <a name="remarks"></a>Observaciones

Para obtener más información sobre los números de esquema, vea la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObject:: GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
