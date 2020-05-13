---
title: Estructura CRuntimeClass
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: a58b9c97d5683423a0f81f6b5424f19f987943bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318559"
---
# <a name="cruntimeclass-structure"></a>Estructura CRuntimeClass

Cada clase derivada `CObject` está asociada `CRuntimeClass` a una estructura que puede utilizar para obtener información sobre un objeto o su clase base en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
struct CRuntimeClass
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|Crea un objeto durante el tiempo de ejecución.|
|[CRuntimeClass::FromName](#fromname)|Crea un objeto durante el tiempo de ejecución utilizando el nombre de clase familiar.|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Determina si la clase se deriva de la clase especificada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Nombre de la clase.|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Tamaño del objeto en bytes.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Un puntero `CRuntimeClass` a la estructura de la clase base.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Puntero a la función que crea dinámicamente el objeto.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Devuelve `CRuntimeClass` la estructura (solo disponible cuando está vinculado dinámicamente).|
|[CRuntimeClass::m_wSchema](#m_wschema)|El número de esquema de la clase.|

## <a name="remarks"></a>Observaciones

`CRuntimeClass`es una estructura y por lo tanto no tiene una clase base.

La capacidad de determinar la clase de un objeto en tiempo de ejecución es útil cuando se necesita una comprobación de tipos adicional de argumentos de función o cuando se debe escribir código de propósito especial basado en la clase de un objeto. La información de clase en tiempo de ejecución no es compatible directamente con el lenguaje C++.

`CRuntimeClass`proporciona información sobre el objeto C++ relacionado, `CRuntimeClass` como un puntero a la clase base y el nombre de clase ASCII de la clase relacionada. Esta estructura también implementa varias funciones que se pueden utilizar para crear objetos dinámicamente, especificando el tipo de objeto mediante un nombre familiar y determinando si la clase relacionada se deriva de una clase específica.

Para obtener más `CRuntimeClass`información sobre el uso , consulte el artículo Acceso a la información de clase en [tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CRuntimeClass`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cruntimeclasscreateobject"></a><a name="createobject"></a>CRuntimeClass::CreateObject

Llame a esta función para crear dinámicamente la clase especificada durante el tiempo de ejecución.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
El nombre familiar de la clase que se va a crear.

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto recién creado, o NULL si no se encuentra el nombre de clase o no hay memoria suficiente para crear el objeto.

### <a name="remarks"></a>Observaciones

Las clases `CObject` derivadas de pueden admitir la creación dinámica, que es la capacidad de crear un objeto de una clase especificada en tiempo de ejecución. Las clases de documento, vista y marco, por ejemplo, deben admitir la creación dinámica. Para obtener más información `CreateObject` sobre la creación dinámica y el miembro, vea [CObject Class](../../mfc/using-cobject.md) y [CObject Class: Specifying Levels of Functionality](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassfromname"></a><a name="fromname"></a>CRuntimeClass::FromName

Llame a esta `CRuntimeClass` función para recuperar la estructura asociada con el nombre familiar.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
El nombre familiar de una `CObject`clase derivada de .

### <a name="return-value"></a>Valor devuelto

Puntero a `CRuntimeClass` un objeto, correspondiente al nombre tal como se pasa en *lpszClassName*. La función devuelve NULL si no se encontró ningún nombre de clase coincidente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

## <a name="cruntimeclassisderivedfrom"></a><a name="isderivedfrom"></a>CRuntimeClass::IsDerivedFrom

Llame a esta función para determinar si la clase de llamada se deriva de la clase especificada en el *pBaseClass* parámetro.

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Parámetros

*pBaseClass*<br/>
El nombre familiar de una `CObject`clase derivada de .

### <a name="return-value"></a>Valor devuelto

TRUESi la `IsDerivedFrom` clase que llama se `CRuntimeClass` deriva de la clase base cuya estructura se proporciona como un parámetro; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

La relación se determina por "caminar" desde la clase del miembro hasta la cadena de clases derivadas hasta la cima. Esta función solo devuelve FALSE si no se encuentra ninguna coincidencia para la clase base.

> [!NOTE]
> Para utilizar `CRuntimeClass` la estructura, debe incluir la macro IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE o IMPLEMENT_SERIAL en la implementación de la clase para la que desea recuperar información de objeto en tiempo de ejecución.

Para obtener más `CRuntimeClass`información sobre el uso de , vea el artículo [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

## <a name="cruntimeclassm_lpszclassname"></a><a name="m_lpszclassname"></a>CRuntimeClass::m_lpszClassName

Cadena terminada en null que contiene el nombre de clase ASCII.

### <a name="remarks"></a>Observaciones

Este nombre se puede utilizar para crear `FromName` una instancia de la clase mediante la función miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_nobjectsize"></a><a name="m_nobjectsize"></a>CRuntimeClass::m_nObjectSize

El tamaño del objeto, en bytes.

### <a name="remarks"></a>Observaciones

Si el objeto tiene miembros de datos que apuntan a la memoria asignada, no se incluye el tamaño de esa memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_pbaseclass"></a><a name="m_pbaseclass"></a>CRuntimeClass::m_pBaseClass

Si la aplicación se vincula estáticamente a MFC, `CRuntimeClass` este miembro de datos contiene un puntero a la estructura de la clase base.

### <a name="remarks"></a>Observaciones

Si la aplicación se vincula dinámicamente a la biblioteca MFC, vea [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_pfncreateobject"></a><a name="m_pfncreateobject"></a>CRuntimeClass::m_pfnCreateObject

Puntero de función al constructor predeterminado que crea un objeto de la clase.

### <a name="remarks"></a>Observaciones

Este puntero solo es válido si la clase admite la creación dinámica; de lo contrario, la función devuelve NULL.

## <a name="cruntimeclassm_pfngetbaseclass"></a><a name="m_pfngetbaseclass"></a>CRuntimeClass::m_pfnGetBaseClass

Si la aplicación usa la biblioteca MFC como un archivo DLL `CRuntimeClass` compartido, este miembro de datos apunta a una función que devuelve la estructura de la clase base.

### <a name="remarks"></a>Observaciones

Si la aplicación se vincula estáticamente a la biblioteca MFC, vea [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_wschema"></a><a name="m_wschema"></a>CRuntimeClass::m_wSchema

El número de esquema ( -1 para las clases no serializables).

### <a name="remarks"></a>Observaciones

Para obtener más información sobre los números de esquema, consulte la [macro IMPLEMENT_SERIAL.](run-time-object-model-services.md#implement_serial)

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
