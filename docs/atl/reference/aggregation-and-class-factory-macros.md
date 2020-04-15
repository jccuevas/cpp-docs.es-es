---
title: Macros de fábrica de clases y agregación
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 33f33043d1a2c824ada26399365541796178d21d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319337"
---
# <a name="aggregation-and-class-factory-macros"></a>Macros de fábrica de clases y agregación

Estas macros proporcionan formas de controlar la agregación y de declarar generadores de clases.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Declara que el objeto se puede agregar (el valor predeterminado).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Declara el generador de clases como [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), el generador de clases predeterminado ATL.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Declara que el objeto de fábrica de clases es el generador de clases.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) como el generador de clases.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) como el generador de clases.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Declara una `GetControllingUnknown` función virtual.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Declara que el objeto no se puede agregar.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Declara que el objeto debe agregarse.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Comprueba el valor del desconocido externo y declara que el objeto se puede agregar o no, según corresponda.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Protege el objeto externo de la eliminación durante la construcción de un objeto interno.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Especifica los indicadores VIEWSTATUS en el contenedor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Especifica que el objeto se puede agregar.

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre de la clase que está definiendo como agregable.

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene esta macro para especificar el modelo de agregación predeterminado. Para invalidar este valor predeterminado, especifique la [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) o [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) macro en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases.

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) utiliza esta macro para declarar el generador de clases predeterminado para el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>Clase CComClassFactory

Esta clase implementa el [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz.

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Observaciones

`CComClassFactory`implementa la interfaz [IClassFactory,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) que contiene métodos para crear un objeto de un CLSID determinado, así como bloquear el generador de clases en la memoria para permitir que se creen nuevos objetos más rápidamente. `IClassFactory`debe implementarse para cada clase que registre en el registro del sistema y a la que asigne un CLSID.

Los objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye [DECLARE_CLASSFACTORY](#declare_classfactory)la macro `CComClassFactory` DECLARE_CLASSFACTORY , que declara como generador de clases predeterminado. Para invalidar este valor predeterminado, especifique una de las macros*DECLARE_CLASSFACTORY XXX* en la definición de clase. Por ejemplo, la macro [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) utiliza la clase especificada para el generador de clases:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

La definición de `CMyClassFactory` clase anterior especifica que se usará como generador de clases predeterminado del objeto. `CMyClassFactory`debe derivar `CComClassFactory` de `CreateInstance`y anular .

ATL proporciona otras tres macros que declaran un generador de clases:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Utiliza [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Utiliza [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios apartamentos.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Utiliza [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye un único [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto.

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

Declara `cf` ser la fábrica de clases.

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parámetros

*Cf*<br/>
[en] El nombre de la clase que implementa el objeto de generador de clases.

### <a name="remarks"></a>Observaciones

El *cf* cf parámetro debe derivar de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) e invalidar el `CreateInstance` método.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la macro [DECLARE_CLASSFACTORY,](#declare_classfactory) que especifica como el generador de clases `CComClassFactory` predeterminado. Sin embargo, al incluir la macro DECLARE_CLASSFACTORY_EX en la definición de clase del objeto, se reemplaza este valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) como el generador de clases.

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parámetros

*Lic*<br/>
[en] Una clase que `VerifyLicenseKey` `GetLicenseKey`implementa `IsLicenseValid`, , y .

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [macro DECLARE_CLASSFACTORY,](#declare_classfactory) que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Sin embargo, al incluir la macro DECLARE_CLASSFACTORY2 en la definición de clase del objeto, invalida este valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>Clase CComClassFactory2

Esta clase implementa la interfaz [IClassFactory2.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parámetros

*Licencia*<br/>
Clase que implementa las siguientes funciones estáticas:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Observaciones

`CComClassFactory2`implementa la interfaz [IClassFactory2,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) que es una extensión de [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`controla la creación de objetos a través de una licencia. Un generador de clases que se ejecuta en un equipo con licencia puede proporcionar una clave de licencia en tiempo de ejecución. Esta clave de licencia permite a una aplicación crear instancias de objetos cuando no existe una licencia de máquina completa.

Los objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la [macro DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Para `CComClassFactory2`utilizar , especifique la [macro DECLARE_CLASSFACTORY2](#declare_classfactory2) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, el parámetro `CComClassFactory2`de plantilla a `VerifyLicenseKey` `GetLicenseKey`, `IsLicenseValid`debe implementar las funciones estáticas , , y . A continuación se muestra un ejemplo de una clase de licencia simple:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`deriva tanto `CComClassFactory2Base` de la *licencia.* `CComClassFactory2Base`, a su vez, deriva de `IClassFactory2` y **CComObjectRootEx\< CComGlobalsThreadModel >**.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases.

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [macro DECLARE_CLASSFACTORY,](#declare_classfactory) que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Sin embargo, al incluir la macro DECLARE_CLASSFACTORY_AUTO_THREAD en la definición de clase del objeto, se reemplaza este valor predeterminado.

Al crear objetos en varios apartamentos (en un servidor fuera de proceso), agregue DECLARE_CLASSFACTORY_AUTO_THREAD a la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>Clase CComClassFactoryAutoThread

Esta clase implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) y permite crear objetos en varios apartamentos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Observaciones

`CComClassFactoryAutoThread`es similar a [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), pero permite crear objetos en varios apartamentos. Para aprovechar esta compatibilidad, derive el módulo EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Los objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la [macro DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Para `CComClassFactoryAutoThread`utilizar , especifique la [macro DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) como el generador de clases.

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
[en] El nombre del objeto de clase.

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [macro DECLARE_CLASSFACTORY,](#declare_classfactory) que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Sin embargo, al incluir la macro DECLARE_CLASSFACTORY_SINGLETON en la definición de clase del objeto, se reemplaza este valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>Clase CComClassFactorySingleton

Esta clase deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un único objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tu clase.

`CComClassFactorySingleton`deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un único objeto. Cada llamada `CreateInstance` al método simplemente consulta este objeto para un puntero de interfaz.

### <a name="remarks"></a>Observaciones

Los objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye [DECLARE_CLASSFACTORY](#declare_classfactory)la macro `CComClassFactory` DECLARE_CLASSFACTORY , que declara como generador de clases predeterminado. Para `CComClassFactorySingleton`utilizar , especifique la [macro DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Declara una función `GetControllingUnknown`virtual .

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Observaciones

Agregue esta macro al objeto si obtiene `GetControllingUnknown` el mensaje de error `CComAggregateCreator`del compilador que no está definido (por ejemplo, en ).

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Especifica que el objeto no se puede agregar.

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre del objeto de clase que está definiendo como no agregable.

### <a name="remarks"></a>Observaciones

DECLARE_NOT_AGGREGATABLE `CreateInstance` hace que se devuelva un error (CLASS_E_NOAGGREGATION) si se intenta agregar al objeto.

De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene la [macro DECLARE_AGGREGATABLE,](#declare_aggregatable) que especifica que se puede agregar el objeto. Para invalidar este comportamiento predeterminado, incluya DECLARE_NOT_AGGREGATABLE en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Especifica que el objeto debe agregarse.

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre del objeto de clase que está definiendo como solo agregable.

### <a name="remarks"></a>Observaciones

DECLARE_ONLY_AGGREGATABLE produce un error (E_FAIL) si `CoCreate` se intenta con el objeto como objeto no agregado.

De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene la [macro DECLARE_AGGREGATABLE,](#declare_aggregatable) que especifica que se puede agregar el objeto. Para invalidar este comportamiento predeterminado, incluya DECLARE_ONLY_AGGREGATABLE en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Especifica que se crea una instancia de **CComPolyObject \< ** *x* **>** cuando se crea el objeto.

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre del objeto de clase que está definiendo como agregable o no agregable.

### <a name="remarks"></a>Observaciones

Durante la creación, se comprueba el valor de la incógnita externa. Si es NULL, `IUnknown` se implementa para un objeto no agregado. Si el desconocido externo `IUnknown` no es NULL, se implementa para un objeto agregado.

La ventaja de usar DECLARE_POLY_AGGREGATABLE es `CComAggObject` `CComObject` que evita tener ambos y en el módulo para controlar los casos agregados y no agregados. Un `CComPolyObject` solo objeto controla ambos casos. Esto significa que sólo una copia de la vtable y una copia de las funciones existen en el módulo. Si su vtable es grande, esto puede disminuir sustancialmente el tamaño del módulo. Sin embargo, si la `CComPolyObject` vtable es pequeña, el uso puede dar lugar a un tamaño de `CComAggObject` `CComObject`módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, tal como son y .

La macro DECLARE_POLY_AGGREGATABLE se declara automáticamente en el objeto si utiliza el Asistente para controles ATL para crear un control completo.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Protege el objeto de ser eliminado si (durante [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) el objeto agregado interno incrementa el recuento de referencias y, a continuación, reduce el recuento a 0.

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Coloque esta macro en la clase de control de un control ActiveX ATL para especificar los indicadores VIEWSTATUS en el contenedor.

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parámetros

*statusFlags*<br/>
[en] Las marcas VIEWSTATUS. Consulte [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) para obtener una lista de indicadores.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
