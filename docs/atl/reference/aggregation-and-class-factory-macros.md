---
title: Macros de agregación y generador de clases
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
ms.openlocfilehash: 554210ab0a26bc54a716a389a1660c4cbd42a209
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168662"
---
# <a name="aggregation-and-class-factory-macros"></a>Macros de agregación y generador de clases

Estas macros proporcionan formas de controlar la agregación y de declarar generadores de clases.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Declara que el objeto se puede Agregar (el valor predeterminado).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Declara que el generador de clases es [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), el generador de clases predeterminado ATL.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Declara el objeto de generador de clases para que sea el generador de clases.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) para que sea el generador de clases.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) para que sea el generador de clases.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) para que sea el generador de clases.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Declara una función virtual `GetControllingUnknown` .|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Declara que el objeto no se puede Agregar.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Declara que se debe agregar el objeto.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Comprueba el valor de la desconocida externa y declara el objeto que se va a agregar o no, según corresponda.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Protege el objeto externo de la eliminación durante la construcción de un objeto interno.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Especifica las marcas VIEWSTATUS para el contenedor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Especifica que el objeto se puede Agregar.

```cpp
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Nombre de la clase que se va a definir como agregable.

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene esta macro para especificar el modelo de agregación predeterminado. Para invalidar este valor predeterminado, especifique la macro [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) o [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) para que sea el generador de clases.

```cpp
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) usa esta macro para declarar el generador de clases predeterminado para el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>Clase CComClassFactory

Esta clase implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .

```cpp
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Observaciones

`CComClassFactory`implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) , que contiene métodos para crear un objeto de un CLSID determinado, así como el bloqueo del generador de clases en la memoria para permitir que se creen nuevos objetos más rápidamente. `IClassFactory`debe implementarse para cada clase que se registre en el registro del sistema y a la que se asigne un CLSID.

Normalmente, los objetos ATL adquieren un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara `CComClassFactory` como el generador de clases predeterminado. Para invalidar este valor predeterminado, especifique una de las macros DECLARE_CLASSFACTORY*XXX* en la definición de clase. Por ejemplo, la macro [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) usa la clase especificada para el generador de clases:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

La definición de clase anterior especifica `CMyClassFactory` que se usará como generador de clases predeterminado del objeto. `CMyClassFactory`debe derivar `CComClassFactory` de e `CreateInstance`invalidar.

ATL proporciona otras tres macros que declaran un generador de clases:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Usa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Usa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios apartamentos.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Usa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye un solo objeto [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) .

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

Declara `cf` como el generador de clases.

```cpp
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parámetros

*Nº*<br/>
de Nombre de la clase que implementa el objeto de generador de clases.

### <a name="remarks"></a>Observaciones

El parámetro *CF* debe derivar de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) e invalidar el `CreateInstance` método.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory) , que especifica `CComClassFactory` como el generador de clases predeterminado. Sin embargo, si se incluye la macro DECLARE_CLASSFACTORY_EX en la definición de clase del objeto, se invalida este valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) para que sea el generador de clases.

```cpp
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parámetros

*Internacional*<br/>
de Una clase que implementa `VerifyLicenseKey`, `GetLicenseKey`y. `IsLicenseValid`

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory) , que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Sin embargo, si se incluye la macro DECLARE_CLASSFACTORY2 en la definición de clase del objeto, se invalida este valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>Clase CComClassFactory2

Esta clase implementa la interfaz [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .

```cpp
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parámetros

*sin*<br/>
Una clase que implementa las siguientes funciones estáticas:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Observaciones

`CComClassFactory2`implementa la interfaz [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) , que es una extensión de [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`controla la creación de objetos a través de una licencia. Un generador de clases que se ejecute en una máquina con licencia puede proporcionar una clave de licencia en tiempo de ejecución. Esta clave de licencia permite a una aplicación crear instancias de objetos cuando no existe una licencia completa de la máquina.

Normalmente, los objetos ATL adquieren un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Para usar `CComClassFactory2`, especifique el [DECLARE_CLASSFACTORY2](#declare_classfactory2) macro en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, el parámetro de plantilla `CComClassFactory2`en, debe implementar las funciones `VerifyLicenseKey`estáticas `GetLicenseKey`, `IsLicenseValid`y. A continuación se facilita un ejemplo de una clase de licencia simple:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`deriva de `CComClassFactory2Base` y de la *licencia*. `CComClassFactory2Base`, a su vez, deriva de `IClassFactory2` y **CComObjectRootEx\< CComGlobalsThreadModel >**.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) para que sea el generador de clases.

```cpp
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory) , que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Sin embargo, si se incluye la macro DECLARE_CLASSFACTORY_AUTO_THREAD en la definición de clase del objeto, se invalida este valor predeterminado.

Al crear objetos en varios apartamentos (en un servidor fuera de proceso), agregue DECLARE_CLASSFACTORY_AUTO_THREAD a la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>Clase CComClassFactoryAutoThread

Esta clase implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) y permite crear objetos en varios apartamentos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

```cpp
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Observaciones

`CComClassFactoryAutoThread`es similar a [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), pero permite crear objetos en varios apartamentos. Para aprovechar esta compatibilidad, derive el módulo EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Normalmente, los objetos ATL adquieren un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Para usar `CComClassFactoryAutoThread`, especifique el [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) macro en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) para que sea el generador de clases.

```cpp
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
de Nombre del objeto de clase.

### <a name="remarks"></a>Observaciones

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory) , que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Sin embargo, si se incluye la macro DECLARE_CLASSFACTORY_SINGLETON en la definición de clase del objeto, se invalida este valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>Clase CComClassFactorySingleton

Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un solo objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

```cpp
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase.

`CComClassFactorySingleton`se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un solo objeto. Cada llamada al `CreateInstance` método simplemente consulta este objeto para obtener un puntero de interfaz.

### <a name="remarks"></a>Observaciones

Normalmente, los objetos ATL adquieren un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara `CComClassFactory` como el generador de clases predeterminado. Para usar `CComClassFactorySingleton`, especifique el [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) macro en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Declara una función `GetControllingUnknown`virtual.

```cpp
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Observaciones

Agregue esta macro al objeto si obtiene el mensaje de error del compilador que `GetControllingUnknown` no está definido (por ejemplo `CComAggregateCreator`, en).

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Especifica que el objeto no se puede Agregar.

```cpp
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Nombre del objeto de clase que se va a definir como no agregable.

### <a name="remarks"></a>Observaciones

DECLARE_NOT_AGGREGATABLE provoca `CreateInstance` que se devuelva un error (CLASS_E_NOAGGREGATION) si se realiza un intento de agregar en el objeto.

De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene la macro [DECLARE_AGGREGATABLE](#declare_aggregatable) , que especifica que se puede Agregar el objeto. Para invalidar este comportamiento predeterminado, incluya DECLARE_NOT_AGGREGATABLE en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Especifica que debe agregarse el objeto.

```cpp
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Nombre del objeto de clase que se va a definir como solo agregado.

### <a name="remarks"></a>Observaciones

DECLARE_ONLY_AGGREGATABLE produce un error (E_FAIL) si se realiza un intento en `CoCreate` el objeto como objeto no agregado.

De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene la macro [DECLARE_AGGREGATABLE](#declare_aggregatable) , que especifica que se puede Agregar el objeto. Para invalidar este comportamiento predeterminado, incluya DECLARE_ONLY_AGGREGATABLE en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Especifica que se crea una instancia de **CComPolyObject \< ** *x* **>** cuando se crea el objeto.

```cpp
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Nombre del objeto de clase que se va a definir como agregable o no agregable.

### <a name="remarks"></a>Observaciones

Durante la creación, se comprueba el valor de la desconocido externa. Si es NULL, `IUnknown` se implementa para un objeto no agregado. Si el desconocido externo no es NULL, `IUnknown` se implementa para un objeto agregado.

La ventaja de usar DECLARE_POLY_AGGREGATABLE es evitar tener `CComAggObject` y `CComObject` en el módulo para controlar los casos agregados y no agregados. Un solo `CComPolyObject` objeto controla ambos casos. Esto significa que solo hay una copia de la tabla vtable y una copia de las funciones en el módulo. Si su vtable es grande, esto puede reducir considerablemente el tamaño del módulo. Sin embargo, si la tabla vtable es pequeña `CComPolyObject` , el uso de puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no `CComAggObject` agregado `CComObject`, como son y.

La macro DECLARE_POLY_AGGREGATABLE se declara automáticamente en el objeto si se utiliza el Asistente para controles ATL para crear un control completo.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Protege el objeto para que no se elimine si (durante [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) el objeto agregado interno incrementa el recuento de referencias y, a continuación, disminuye el recuento a 0.

```cpp
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Coloque esta macro en una clase de control del control ActiveX ATL para especificar las marcas VIEWSTATUS en el contenedor.

```cpp
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parámetros

*statusFlags*<br/>
de Marcas de VIEWSTATUS. Consulte [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) para obtener una lista de marcas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
