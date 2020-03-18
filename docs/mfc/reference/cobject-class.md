---
title: CObject (clase)
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
ms.openlocfilehash: 515c4e90ee6ab77a6c7c1ae108393ea1aafb7c17
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424024"
---
# <a name="cobject-class"></a>CObject (clase)

La clase base principal para la biblioteca de MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CObject:: CObject](#cobject)|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObject:: AssertValid](#assertvalid)|Valida la integridad de este objeto.|
|[CObject::D UMP](#dump)|Genera un volcado de diagnóstico de este objeto.|
|[CObject:: GetRuntimeClass](#getruntimeclass)|Devuelve la estructura de `CRuntimeClass` correspondiente a la clase de este objeto.|
|[CObject:: IsKindOf](#iskindof)|Comprueba la relación de este objeto con una clase determinada.|
|[CObject:: IsSerializable](#isserializable)|Comprueba si este objeto se puede serializar.|
|[CObject:: Serialize](#serialize)|Carga o almacena un objeto de o en un archivo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObject:: operator delete](#operator_delete)|Operador de **eliminación** especial.|
|[CObject:: Operator New](#operator_new)|Operador **New** especial.|

## <a name="remarks"></a>Observaciones

Actúa como la raíz no solo para las clases de biblioteca como `CFile` y `CObList`, sino también para las clases que se escriben. `CObject` proporciona servicios básicos, incluidos

- Compatibilidad con la serialización

- Información de clase en tiempo de ejecución

- Salida de diagnóstico de objetos

- Compatibilidad con las clases de colección

Tenga en cuenta que `CObject` no admite la herencia múltiple. Las clases derivadas solo pueden tener una `CObject` clase base, y esa `CObject` debe estar más a la izquierda en la jerarquía. Sin embargo, se permite que las estructuras y las clases derivadas de no `CObject`en bifurcaciones de herencia múltiple a la derecha.

Obtendrá ventajas importantes de la derivación de `CObject` si usa algunas de las macros opcionales en la implementación y las declaraciones de clase.

Las macros de primer nivel, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) y [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), permiten el acceso en tiempo de ejecución al nombre de la clase y su posición en la jerarquía. Esto, a su vez, permite un volcado de diagnóstico significativo.

Las macros de segundo nivel, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), incluyen toda la funcionalidad de las macros de primer nivel y permiten que un objeto se "serialice" hacia y desde un "archivo".

Para obtener información sobre cómo derivar clases y C++ clases de Microsoft Foundation en general y utilizar `CObject`, vea [usar CObject](../../mfc/using-cobject.md) y [serialización](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="assertvalid"></a>CObject:: AssertValid

Valida la integridad de este objeto.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Observaciones

`AssertValid` realiza una comprobación de validez en este objeto comprobando su estado interno. En la versión de depuración de la biblioteca, `AssertValid` puede afirmar y, por tanto, terminar el programa con un mensaje que muestra el número de línea y el nombre de archivo donde se produjo un error en la aserción.

Al escribir su propia clase, debe invalidar la función `AssertValid` para proporcionar servicios de diagnóstico a sí mismo y a otros usuarios de su clase. El `AssertValid` invalidado normalmente llama a la función `AssertValid` de su clase base antes de comprobar los miembros de datos únicos de la clase derivada.

Dado que `AssertValid` es una función **const** , no se le permite cambiar el estado del objeto durante la prueba. Su propia clase derivada `AssertValid` funciones no deben producir excepciones, sino que deben validar si detectan datos de objetos no válidos.

La definición de "validez" depende de la clase del objeto. Como regla, la función debe realizar una "comprobación superficial". Es decir, si un objeto contiene punteros a otros objetos, debe comprobar si los punteros no son NULL, pero no debe realizar pruebas de validez en los objetos a los que hacen referencia los punteros.

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Para ver otro ejemplo, vea [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

##  <a name="cobject"></a>CObject:: CObject

Estas funciones son los constructores de `CObject` estándar.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parámetros

*objectSrc*<br/>
Referencia a otro `CObject`

### <a name="remarks"></a>Observaciones

El constructor de la clase derivada llama automáticamente a la versión predeterminada.

Si la clase es serializable (incorpora la macro IMPLEMENT_SERIAL), debe tener un constructor predeterminado (un constructor sin argumentos) en la declaración de clase. Si no necesita un constructor predeterminado, declare un constructor "Empty" privado o protegido. Para obtener más información, vea [usar CObject](../../mfc/using-cobject.md).

El constructor C++ de copias de clase predeterminado estándar realiza una copia miembro por miembro. La presencia del constructor de copias de `CObject` privado garantiza un mensaje de error del compilador si se necesita el constructor de copias de la clase, pero no está disponible. Por lo tanto, debe proporcionar un constructor de copias si la clase requiere esta funcionalidad.

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>CObject::D UMP

Vuelca el contenido del objeto en un objeto [CDumpContext](../../mfc/reference/cdumpcontext-class.md) .

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
Contexto de volcado de diagnóstico para el volcado, normalmente `afxDump`.

### <a name="remarks"></a>Observaciones

Al escribir su propia clase, debe invalidar la función `Dump` para proporcionar servicios de diagnóstico a sí mismo y a otros usuarios de su clase. El `Dump` invalidado normalmente llama a la función `Dump` de su clase base antes de imprimir miembros de datos únicos de la clase derivada. `CObject::Dump` imprime el nombre de clase si la clase usa la macro `IMPLEMENT_DYNAMIC` o IMPLEMENT_SERIAL.

> [!NOTE]
>  La función `Dump` no debe imprimir un carácter de nueva línea al final de la salida.

`Dump` llamadas solo tienen sentido en la versión de depuración de la biblioteca MFC. Debe corchetes de llamadas, declaraciones de función e implementaciones de funciones con **#ifdef _DEBUG**/ instrucciones de `#endif` para la compilación condicional.

Como `Dump` es una función **const** , no se le permite cambiar el estado del objeto durante el volcado.

El [operador de inserción CDumpContext (< <)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) llama a `Dump` cuando se inserta un puntero de `CObject`.

`Dump` solo permite el volcado "acíclicos" de objetos. Puede volcar una lista de objetos, por ejemplo, pero si uno de los objetos es la propia lista, finalmente desbordará la pila.

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>CObject:: GetRuntimeClass

Devuelve la estructura de `CRuntimeClass` correspondiente a la clase de este objeto.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) correspondiente a la clase de este objeto; nunca **es null**.

### <a name="remarks"></a>Observaciones

Hay una estructura de `CRuntimeClass` para cada clase derivada de `CObject`. Los miembros de la estructura son los siguientes:

- **M_lpszClassName LPCSTR** Una cadena terminada en null que contiene el nombre de clase ASCII.

- **int m_nObjectSize** Tamaño del objeto, en bytes. Si el objeto tiene miembros de datos que apuntan a la memoria asignada, no se incluye el tamaño de esa memoria.

- **M_wSchema uint** El número de esquema (-1 para clases no serializables). Vea la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) para obtener una descripción del número de esquema.

- **\* CObject (m_pfnCreateObject de\* Pascal) ()** Un puntero de función al constructor predeterminado que crea un objeto de la clase (solo es válido si la clase admite la creación dinámica; de lo contrario, devuelve **null**).

- **\* CRuntimeClass (m_pfn_GetBaseClass de\* Pascal) ()** Si la aplicación está vinculada dinámicamente a la versión de AFXDLL de MFC, un puntero a una función que devuelve la estructura `CRuntimeClass` de la clase base.

- **CRuntimeClass\* m_pBaseClass** Si la aplicación está vinculada estáticamente a MFC, un puntero a la estructura de `CRuntimeClass` de la clase base.

Esta función requiere el uso de la macro [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)o [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) en la implementación de la clase. De lo contrario, obtendrá resultados incorrectos.

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>CObject:: IsKindOf

Comprueba la relación de este objeto con una clase determinada.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parámetros

*pClass*<br/>
Puntero a una estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociada a la clase derivada de `CObject`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto corresponde a la clase; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función prueba *pClass* para ver si (1) es un objeto de la clase especificada o (2) es un objeto de una clase derivada de la clase especificada. Esta función solo funciona para las clases declaradas con la macro [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)o [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) .

No use esta función en gran medida porque anula la característica de C++ polimorfismo. En su lugar, use funciones virtuales.

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>CObject:: IsSerializable

Comprueba si este objeto es válido para la serialización.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si este objeto se puede serializar; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Para que una clase sea serializable, su declaración debe contener la macro [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) y la implementación debe contener la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

> [!NOTE]
>  No invalide esta función.

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>CObject:: operator delete

Para la versión de lanzamiento de la biblioteca, el operador **Delete** libera la memoria asignada por el operador **New**.

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

En la versión de depuración, el operador **Delete** participa en un esquema de supervisión de asignación diseñado para detectar pérdidas de memoria.

Si usa la línea de código

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

antes de cualquiera de las implementaciones en un. Archivo CPP, se usará la tercera versión de **Delete** , almacenando el nombre de archivo y el número de línea en el bloque asignado para los informes posteriores. No tiene que preocuparse de proporcionar los parámetros adicionales. una macro se encarga de ello.

Incluso si no usa DEBUG_NEW en modo de depuración, todavía obtendrá la detección de pérdidas, pero sin los informes de número de línea del archivo de origen descritos anteriormente.

Si invalida los operadores **New** y **Delete**, perderá esta funcionalidad de diagnóstico.

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>CObject:: Operator New

Para la versión de lanzamiento de la biblioteca, el operador **New** realiza una asignación de memoria óptima de manera similar a `malloc`.

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Observaciones

En la versión de depuración, el operador **New** participa en un esquema de supervisión de asignación diseñado para detectar pérdidas de memoria.

Si usa la línea de código

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

antes de cualquiera de las implementaciones en un. Archivo CPP, se usará la segunda versión de **New** , almacenando el nombre de archivo y el número de línea en el bloque asignado para los informes posteriores. No tiene que preocuparse de proporcionar los parámetros adicionales. una macro se encarga de ello.

Incluso si no usa DEBUG_NEW en modo de depuración, todavía obtendrá la detección de pérdidas, pero sin los informes de número de línea del archivo de origen descritos anteriormente.

> [!NOTE]
>  Si invalida este operador, también debe invalidar la **eliminación**. No utilice la función de `_new_handler` de la biblioteca estándar.

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>CObject:: Serialize

Lee o escribe este objeto de o en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*analítico*<br/>
`CArchive` objeto que se va a serializar o desde el que se va a serializar.

### <a name="remarks"></a>Observaciones

Debe reemplazar `Serialize` por cada clase que desee serializar. El `Serialize` invalidado debe llamar primero a la función `Serialize` de su clase base.

También debe utilizar la macro [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) en la declaración de clase y debe utilizar la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) en la implementación de.

Use [CArchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading) o [CArchive:: IsStoring](../../mfc/reference/carchive-class.md#isstoring) para determinar si el archivo se está cargando o almacenando.

[CArchive:: ReadObject](../../mfc/reference/carchive-class.md#readobject) y [CArchive:: WriteObject](../../mfc/reference/carchive-class.md#writeobject)llaman a `Serialize`. Estas funciones están asociadas con el operador de inserción `CArchive` ( **<\<** ) y el operador de extracción ( **>>** ).

Para obtener ejemplos de serialización, vea el artículo [serialización: serializar un objeto](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de `CObject`.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
