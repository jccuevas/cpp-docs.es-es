---
title: Macros de opciones de compilador
ms.date: 11/04/2016
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: d0da6ebcb178735fc25c656241fe23497d941ab6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631158"
---
# <a name="compiler-options-macros"></a>Macros de opciones de compilador

Estas macros controlan las características específicas del compilador.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Convierte un símbolo que habilita los errores en los proyectos desde versiones anteriores de ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Define si uno o varios de los objetos utilizan el apartamento de subproceso.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Hace que determinados `CString` constructores explícitos, impidiendo cualquier conversión involuntaria.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Definir esta macro para poder usar estándar compatible con sintaxis de C++, que genera el error del compilador C4867 cuando se usa una sintaxis no estándar para inicializar un puntero a una función miembro.|
|[ACTIVA _ATL_FREE_THREADED](#_atl_free_threaded)|Define si uno o varios de los objetos utilizan el subprocesamiento libre o neutra.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Un símbolo que indica el proyecto tendrá los objetos que están marcados como ambos, libre o neutra. La macro [activa _ATL_FREE_THREADED](#_atl_free_threaded) debe usarse en su lugar.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Un símbolo que impide el uso predeterminado de espacio de nombres como ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Un símbolo que impide que el código relacionado con COM que se está compilando el proyecto.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Un símbolo que impide que el puntero vtable que se inicializa en el constructor y destructor de la clase.|
|[ATL_NOINLINE](#atl_noinline)|Un símbolo que indica una función no debe estar entre línea.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Define si todos los objetos utilizan el modelo de subprocesamiento único.|

##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS

Convierte un símbolo que habilita los errores en los proyectos desde versiones anteriores de ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Comentarios

Antes de Visual C++ .NET 2002, ATL había deshabilitado una gran cantidad de advertencias y dejó deshabilitado para que nunca aparecían en el código de usuario. De manera específica:

- C4127 la expresión condicional es constante

- C4786 'identifier': identificador se ha truncado a 'número' caracteres en la información de depuración

- C4201 ha utilizado una extensión no estándar: struct/union sin nombre

- C4103 'filename': utilizado #pragma pack para cambiar la alineación

- C4291 'declaration': no coincidente se encuentra; de operador delete no se liberará memoria si la inicialización produce una excepción

- C4268 'identifier': los datos estáticos/globales 'const' inicializados con el constructor de predeterminado generado por compilador rellenan el objeto con ceros

- Código inalcanzable C4702

En proyectos convertidos desde versiones anteriores, estas advertencias todavía están deshabilitadas de los encabezados de bibliotecas.

Agregando la siguiente línea al archivo stdafx.h antes de incluir encabezados de bibliotecas, se puede cambiar este comportamiento.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Si este `#define` se agrega, los encabezados ATL tienen el cuidado para conservar el estado de estas advertencias para que no estén deshabilitados globalmente (o si el usuario deshabilita de forma explícita las advertencias individuales, para que no puedan).

Nuevos proyectos tienen esto `#define` establecido en stdafx.h de forma predeterminada.

##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED

Define si uno o varios de los objetos utilizan el apartamento de subproceso.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Comentarios

Especifica el apartamento de subproceso. Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para otros subprocesos opciones, y [opciones, Asistente para objetos simples de ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos, los modelos disponibles para un objeto ATL.

##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Hace que determinados `CString` constructores explícitos, impidiendo cualquier conversión involuntaria.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Comentarios

Cuando esto se define, se compilan todos los constructores CString que toman un parámetro único con la palabra clave explícita, lo que impide que las conversiones implícitas de argumentos de entrada. Esto significa, por ejemplo, que cuando se define _UNICODE, si intenta usar una cadena de char * como un argumento de constructor CString, se producirá un error del compilador. Use esta macro en situaciones donde es necesario para evitar conversiones implícitas entre tipos de cadenas anchas y estrechas.

Mediante el uso de la macro _T en todos los argumentos de cadena de constructor, puede definir _ATL_CSTRING_EXPLICIT_CONSTRUCTORS y evitar errores de compilación, independientemente de si se define _UNICODE.

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

Definir esta macro con el fin de forzar el uso de sintaxis compatibles con el estándar de C++ de ANSI para el puntero a las funciones miembro. Utiliza esta macro provocará el error del compilador C4867 generarse cuando se usan la sintaxis no estándar para inicializar un puntero a una función miembro.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Comentarios

Han cambiado las bibliotecas de ATL y MFC para que coincida con la conformidad de C++ estándar mejorada del compilador de Visual C++. Según el estándar ANSI C++, la sintaxis de un puntero a una función miembro de clase debe ser `&CMyClass::MyFunc`.

Cuando [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) no está definido (el caso predeterminado), ATL y MFC deshabilita el error C4867 en mapas de macro (mapas de mensajes en particular) para que pueda continuar el código que se crearon en versiones anteriores crear como antes. Si define **_ATL_ENABLE_PTM_WARNING**, el código debe ser compatible con el estándar de C++.

Sin embargo, el formato no estándar en desuso, por lo que deberá mover código existente a la sintaxis compatible con estándar de C++. Por ejemplo, los elementos siguientes:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Debe cambiarse por:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Tenga en cuenta que para las macros de mapa que agregue el carácter '&', no debe agregarlo nuevo en el código.

##  <a name="_atl_free_threaded"></a>  ACTIVA _ATL_FREE_THREADED

Define si uno o varios de los objetos utilizan el subprocesamiento libre o neutra.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Comentarios

Especifica el subprocesamiento libre. Subprocesamiento libre es equivalente a un modelo de apartamento multiproceso. Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para otros subprocesos opciones, y [opciones, Asistente para objetos simples de ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos, los modelos disponibles para un objeto ATL.

##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED

Un símbolo que indica el proyecto tendrá los objetos que están marcados como ambos, libre o neutra.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Comentarios

Si se define este símbolo, ATL se extrae en el código que se sincronizará correctamente el acceso a datos globales. Código nuevo debe usar la macro equivalente [activa _ATL_FREE_THREADED](#_atl_free_threaded) en su lugar.

##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE

Un símbolo que impide el uso predeterminado de espacio de nombres como ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Comentarios

Si no se define este símbolo, incluidas atlbase.h llevará a cabo **con el espacio de nombres ATL** de forma predeterminada, que puede dar lugar a conflictos de nomenclatura. Para evitar esto, defina este símbolo.

##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT

Un símbolo que impide que el código relacionado con COM que se está compilando el proyecto.

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

Un símbolo que impide que el puntero vtable que se inicializa en el constructor y destructor de la clase.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Comentarios

Si el puntero vtable se impide que se inicializa en el constructor de clase y el destructor, el enlazador puede eliminar la vtable y todas las funciones a la que señala. Se expande a **__declspec (novtable)**.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>  ATL_NOINLINE

Un símbolo que indica una función no debe estar entre línea.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parámetros

*MyFunction*<br/>
La función que no debe estar entre línea.

### <a name="remarks"></a>Comentarios

Utilice este símbolo, si desea asegurarse de que una función no se insertan por el compilador, aunque debe declararse como en línea para que se puede colocar en un archivo de encabezado. Se expande a **__declspec (noinline)**.

##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED

Define si todos los objetos utilizan el modelo de subprocesamiento único

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Comentarios

Especifica que el objeto siempre se ejecuta en el subproceso COM principal. Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para otros subprocesos opciones, y [opciones, Asistente para objetos simples de ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos, los modelos disponibles para un objeto ATL.

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
