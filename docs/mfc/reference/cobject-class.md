---
title: Clase CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: cea4d09a1c1a4680b095a40fa0619287959ff4ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360425"
---
# <a name="cobject-class"></a>Clase CObject

La clase base principal para la biblioteca de MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CObject::CObject](#cobject)|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObject::AssertValid](#assertvalid)|Valida la integridad de este objeto.|
|[CObject::Dump](#dump)|Produce un volcado de diagnóstico de este objeto.|
|[CObject::GetRuntimeClass](#getruntimeclass)|Devuelve `CRuntimeClass` la estructura correspondiente a la clase de este objeto.|
|[CObject::IsKindOf](#iskindof)|Comprueba la relación de este objeto con una clase determinada.|
|[CObject::IsSerializable](#isserializable)|Comprueba si este objeto se puede serializar.|
|[CObject::Serialize](#serialize)|Carga o almacena un objeto desde/hacia un archivo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObject::operator delete](#operator_delete)|Operador de **eliminación** especial.|
|[CObject::operador nuevo](#operator_new)|**Nuevo** operador especial.|

## <a name="remarks"></a>Observaciones

Sirve como raíz no solo para `CFile` las `CObList`clases de biblioteca como y , sino también para las clases que se escriben. `CObject`presta servicios básicos, incluyendo

- Soporte de serialización

- Información de clase en tiempo de ejecución

- Salida de diagnóstico de objetos

- Compatibilidad con clases de colección

Tenga `CObject` en cuenta que no admite la herencia múltiple. Las clases derivadas solo `CObject` pueden tener `CObject` una clase base, y debe estar más a la izquierda en la jerarquía. Sin embargo, es permisible tener estructuras `CObject`y clases no derivadas en ramas de herencia múltiple a la derecha.

Obtendrá los principales `CObject` beneficios de la derivación si utiliza algunas de las macros opcionales en la implementación de la clase y las declaraciones.

Las macros de primer nivel, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) y [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), permiten el acceso en tiempo de ejecución al nombre de clase y su posición en la jerarquía. Esto, a su vez, permite un dumping de diagnóstico significativo.

Las macros de segundo nivel, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), incluyen toda la funcionalidad de las macros de primer nivel y permiten que un objeto se "serializa" hacia y desde un "archivo".

Para obtener información sobre cómo derivar clases de `CObject`Microsoft Foundation y clases C++ en general y using , consulte Uso de [CObject](../../mfc/using-cobject.md) y [serialización](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject::AssertValid

Valida la integridad de este objeto.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Observaciones

`AssertValid`realiza una comprobación de validez en este objeto comprobando su estado interno. En la versión de `AssertValid` depuración de la biblioteca, puede afirmar y, por lo tanto, finalizar el programa con un mensaje que enumera el número de línea y el nombre de archivo donde se produjo un error en la aserción.

Al escribir su propia clase, `AssertValid` debe invalidar la función para proporcionar servicios de diagnóstico para usted y otros usuarios de la clase. El invalidado `AssertValid` normalmente llama a la `AssertValid` función de su clase base antes de comprobar los miembros de datos únicos para la clase derivada.

Dado `AssertValid` que es una función **const,** no se le permite cambiar el estado del objeto durante la prueba. Sus propias `AssertValid` funciones de clase derivada no deben producir excepciones, sino que deben afirmar si detectan datos de objetos no válidos.

La definición de "validez" depende de la clase del objeto. Como regla general, la función debe realizar una "comprobación de poca profundidad." Es decir, si un objeto contiene punteros a otros objetos, debe comprobar si los punteros no son nulos, pero no debe realizar pruebas de validez en los objetos a los que hace referencia los punteros.

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en todos los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Para obtener otro ejemplo, vea [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject::CObject

Estas funciones `CObject` son los constructores estándar.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parámetros

*objectSrc*<br/>
Una referencia a otro`CObject`

### <a name="remarks"></a>Observaciones

El constructor de la clase derivada llama automáticamente a la versión predeterminada.

Si la clase es serializable (incorpora la IMPLEMENT_SERIAL macro), debe tener un constructor predeterminado (un constructor sin argumentos) en la declaración de clase. Si no necesita un constructor predeterminado, declare un constructor "vacío" privado o protegido. Para obtener más información, consulte Uso de [CObject](../../mfc/using-cobject.md).

El constructor de copia de clase predeterminado estándar de C++ realiza una copia miembro por miembro. La presencia del `CObject` constructor de copias privadas garantiza un mensaje de error del compilador si el constructor de copias de la clase es necesario pero no está disponible. Por lo tanto, debe proporcionar un constructor de copias si la clase requiere esta capacidad.

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject::Dump

Vuelca el contenido del objeto en un [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objeto.

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parámetros

*Dc*<br/>
El contexto de volcado de `afxDump`diagnóstico para el volcado, normalmente .

### <a name="remarks"></a>Observaciones

Al escribir su propia clase, `Dump` debe invalidar la función para proporcionar servicios de diagnóstico para usted y otros usuarios de la clase. El invalidado `Dump` normalmente llama a la `Dump` función de su clase base antes de imprimir miembros de datos únicos para la clase derivada. `CObject::Dump`imprime el nombre de clase `IMPLEMENT_DYNAMIC` si la clase utiliza la macro o IMPLEMENT_SERIAL.

> [!NOTE]
> La `Dump` función no debe imprimir un carácter de nueva línea al final de su salida.

`Dump`las llamadas solo tienen sentido en la versión de depuración de la biblioteca Microsoft Foundation Class. Debe entre corchetes llamadas, declaraciones de función e implementaciones de función con **#ifdef _DEBUG** /  `#endif` instrucciones para la compilación condicional.

Puesto `Dump` que es una función **const,** no se le permite cambiar el estado del objeto durante el volcado.

El [CDumpContext operador de inserción (<<)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) llama `Dump` cuando se inserta un `CObject` puntero.

`Dump`sólo permite el vertido "cíclico" de objetos. Puede volcar una lista de objetos, por ejemplo, pero si uno de los objetos es la propia lista, finalmente desbordará la pila.

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en todos los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject::GetRuntimeClass

Devuelve `CRuntimeClass` la estructura correspondiente a la clase de este objeto.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura correspondiente a la clase de este objeto; nunca **NULL**.

### <a name="remarks"></a>Observaciones

Hay una `CRuntimeClass` estructura `CObject`para cada clase derivada. Los miembros de la estructura son los siguientes:

- **m_lpszClassName LPCSTR** Cadena terminada en null que contiene el nombre de clase ASCII.

- **int m_nObjectSize** El tamaño del objeto, en bytes. Si el objeto tiene miembros de datos que apuntan a la memoria asignada, no se incluye el tamaño de esa memoria.

- **m_wSchema UINT** El número de esquema ( - 1 para las clases no serializables). Consulte la [macro de IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) para obtener una descripción del número de esquema.

- **CObject\* (\* PASCAL m_pfnCreateObject )( )** Un puntero de función al constructor predeterminado que crea un objeto de la clase (válido solo si la clase admite la creación dinámica; en caso contrario, devuelve **NULL**).

- **CRuntimeClass\* (\* PASCAL m_pfn_GetBaseClass )( )** Si la aplicación está vinculada dinámicamente a la versión `CRuntimeClass` AFXDLL de MFC, un puntero a una función que devuelve la estructura de la clase base.

- **CRuntimeClass\* m_pBaseClass** Si la aplicación está vinculada estáticamente `CRuntimeClass` a MFC, un puntero a la estructura de la clase base.

Esta función requiere el uso de la [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate), o [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro en la implementación de la clase. De lo contrario, obtendrá resultados incorrectos.

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en todos los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>CObject::IsKindOf

Comprueba la relación de este objeto con una clase determinada.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parámetros

*pClass*<br/>
Puntero a una estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociada a la `CObject`clase derivada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto corresponde a la clase; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función prueba *pClass* para ver si (1) es un objeto de la clase especificada o (2) es un objeto de una clase derivada de la clase especificada. Esta función solo funciona para las clases declaradas con la macro [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)o [DECLARE_SERIAL.](run-time-object-model-services.md#declare_serial)

No utilice esta función extensamente porque derrota la función de polimorfismo C++. Utilice funciones virtuales en su lugar.

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en todos los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject::IsSerializable

Comprueba si este objeto es apto para la serialización.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si este objeto se puede serializar; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para que una clase sea serializable, su declaración debe contener la [macro DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) y la implementación debe contener la [macro IMPLEMENT_SERIAL.](run-time-object-model-services.md#implement_serial)

> [!NOTE]
> No invalide esta función.

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en todos los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject::operator delete

Para la versión Release de la biblioteca, el operador **delete** libera la memoria asignada por el operador **new**.

```
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Observaciones

En la versión de depuración, **la eliminación** del operador participa en un esquema de supervisión de asignación diseñado para detectar pérdidas de memoria.

Si utiliza la línea de código

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

antes de cualquiera de sus implementaciones en un archivo . CPP, entonces se utilizará la tercera versión de **delete,** almacenando el nombre de archivo y el número de línea en el bloque asignado para informes posteriores. No tiene que preocuparse por suministrar los parámetros adicionales; una macro se encarga de eso por usted.

Incluso si no utiliza DEBUG_NEW en el modo de depuración, todavía obtiene la detección de fugas, pero sin los informes de número de línea de archivo de origen descritos anteriormente.

Si invalida los operadores **new** y **elimina**, perderá esta capacidad de diagnóstico.

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject::operador nuevo

Para la versión Release **new** de la biblioteca, el operador new `malloc`realiza una asignación de memoria óptima de una manera similar a .

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Observaciones

En la versión de depuración, el operador **new** participa en un esquema de supervisión de asignación diseñado para detectar pérdidas de memoria.

Si utiliza la línea de código

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

antes de cualquiera de sus implementaciones en un archivo . CPP, entonces se utilizará la segunda versión de **new,** almacenando el nombre de archivo y el número de línea en el bloque asignado para informes posteriores. No tiene que preocuparse por suministrar los parámetros adicionales; una macro se encarga de eso por usted.

Incluso si no utiliza DEBUG_NEW en el modo de depuración, todavía obtiene la detección de fugas, pero sin los informes de número de línea de archivo de origen descritos anteriormente.

> [!NOTE]
> Si invalida este operador, también debe invalidar **delete**. No utilice la `_new_handler` función de biblioteca estándar.

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject::Serialize

Lee o escribe este objeto de o en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
Objeto `CArchive` desde o hacia el que serializar.

### <a name="remarks"></a>Observaciones

Debe invalidar `Serialize` para cada clase que desee serializar. El invalidado `Serialize` debe `Serialize` llamar primero a la función de su clase base.

También debe usar la [macro DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) en la declaración de clase y debe usar la [macro IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) en la implementación.

Utilice [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) o [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) para determinar si el archivo se está cargando o almacenando.

`Serialize`es llamado por [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) y [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Estas funciones están `CArchive` asociadas ** < **con el **>>** operador de inserción ( ) y el operador de extracción ( ).

Para obtener ejemplos de serialización, vea el artículo [Serialización: serialización](../../mfc/serialization-serializing-an-object.md)de un objeto .

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista `CObject` de la clase utilizada en todos los ejemplos.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
