---
title: Macros de opciones del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e84c92e8bbf65ff3b8b54111bcce2306628edb1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-options-macros"></a>Opciones del compilador de Macros
Estas macros controlan las características del compilador específico.  
  
|||  
|-|-|  
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Convierte un símbolo que habilita los errores en los proyectos desde versiones anteriores de ATL.|  
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Define si uno o varios de los objetos utilizan el apartamento de subproceso.|  
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Hace que ciertas `CString` constructores explícitos, evitar las conversiones involuntarias.|  
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Definir esta macro para poder usar C++ compatible con la sintaxis estándar, lo que genera el error del compilador C4867 cuando se utiliza una sintaxis no estándar para inicializar un puntero a una función miembro.|  
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Define si uno o varios de los objetos utilizan el subprocesamiento libre o neutral.|  
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Un símbolo que indica el proyecto tendrá los objetos que están marcados como ambos, libre o Neutral. La macro [_ATL_FREE_THREADED](#_atl_free_threaded) debe usarse en su lugar.|  
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Un símbolo que impide el uso predeterminado de espacio de nombres como ATL.|  
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Un símbolo que impide que el código relacionado con COM que se está compilando con el proyecto.|  
|[ATL_NO_VTABLE](#atl_no_vtable)|Un símbolo que impide que el puntero vtable que se inicializa en el constructor y el destructor de la clase.|  
|[ATL_NOINLINE](#atl_noinline)|Un símbolo que indica una función no debe estar entre línea.|  
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Define si todos los objetos utilizan el modelo de subprocesamiento único.|  
  
##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS  
 Convierte un símbolo que habilita los errores en los proyectos desde versiones anteriores de ATL.  
  
```
#define _ATL_ALL_WARNINGS
```  
  
### <a name="remarks"></a>Comentarios  
 Antes de Visual C++ .NET 2002, ATL había deshabilitado una gran cantidad de advertencias y dejaste deshabilitado para que los nunca se muestran en el código de usuario. De manera específica:  
  
-   C4127 la expresión condicional es constante  
  
-   C4786 'identifier': identificador se ha truncado a 'número' caracteres en la información de depuración  
  
-   C4201 ha utilizado una extensión no estándar: struct/union sin nombre  
  
-   C4103 'filename': utilizado #pragma pack para cambiar la alineación  
  
-   C4291 'declaration': ninguna búsqueda de coincidencias operador delete se encuentra; no se liberará memoria si la inicialización produce una excepción  
  
-   C4268 'identifier': los datos estáticos/globales 'const' inicializados con el constructor predeterminado de generados por el compilador rellenan el objeto con ceros  
  
-   Código inalcanzable C4702  
  
 En los proyectos convertidos a partir de versiones anteriores, estas advertencias todavía están deshabilitadas de los encabezados de las bibliotecas.  
  
 Agregando la siguiente línea al archivo stdafx.h antes de incluir encabezados de bibliotecas, este comportamiento se puede cambiar.  
  
 [!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]  
  
 Si este `#define` se agrega, los encabezados ATL son cuidados conservar el estado de estas advertencias para que no estén deshabilitados globalmente (o si el usuario deshabilita explícitamente advertencias individuales, no para habilitarlos).  
  
 Nuevos proyectos tienen este `#define` establecido en stdafx.h de forma predeterminada.  
  
##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED  
 Define si uno o varios de los objetos utilizan el apartamento de subproceso.  
  
```
_ATL_APARTMENT_THREADED
```  
  
### <a name="remarks"></a>Comentarios  
 Especifica el apartamento de subproceso. Vea [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) de otros subprocesos opciones, y [opciones, Asistente para objetos simples de ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos los modelos disponibles para un objeto ATL.  
  
##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS  
 Hace que ciertas `CString` constructores explícitos, evitar las conversiones involuntarias.  
  
```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando esto está definido, se compilan todos los constructores de CString que toman un único parámetro con la palabra clave explícita, lo que impide que las conversiones implícitas de argumentos de entrada. Esto significa, por ejemplo, que cuando se defina _UNICODE, si intenta usar una cadena de char * como un argumento de constructor CString, se producirá un error del compilador. Use esta macro en situaciones donde es necesario evitar conversiones implícitas entre los tipos de cadenas anchas y estrechas.  
  
 Mediante el uso de la macro _T en todos los argumentos de cadena de constructor, puede definir _ATL_CSTRING_EXPLICIT_CONSTRUCTORS y evitar errores de compilación, independientemente de si se ha definido _UNICODE.  
  
##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING  
 Definir esta macro con el fin de forzar el uso de sintaxis compatible con el estándar de C++ de ANSI para el puntero a las funciones miembro. Utiliza esta macro provocará el error del compilador C4867 generarse cuando se utilizan la sintaxis no estándar para inicializar un puntero a una función miembro.  
  
```
#define _ATL_ENABLE_PTM_WARNING
```  
  
### <a name="remarks"></a>Comentarios  
 Han cambiado las bibliotecas ATL y MFC para que coincida con la compatibilidad de C++ estándar mejorada del compilador de Visual C++. Según el estándar ANSI C++, la sintaxis de un puntero a una función de miembro de clase debe ser `&CMyClass::MyFunc`.  
  
 Cuando [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) no está definido (el caso predeterminado), ATL y MFC deshabilita el error C4867 en las asignaciones de macro (mapas de mensajes en particular) para que pueda continuar el código que se crearon en versiones anteriores a generar como antes. Si define **_ATL_ENABLE_PTM_WARNING**, su código debería ser compatible con el estándar de C++.  
  
 Sin embargo, el formulario no estándar está en desuso, por lo que necesita mover el código existente a la sintaxis compatible con estándar de C++. Por ejemplo, la siguiente:  
  
 [!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]  
  
 Debe cambiarse para:  
  
 [!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]  
  
 Tenga en cuenta que para las macros de mapa que agregue el carácter '&', no debe agregarlo nuevo en el código.  
  
##  <a name="_atl_free_threaded"></a>  _ATL_FREE_THREADED  
 Define si uno o varios de los objetos utilizan el subprocesamiento libre o neutral.  
  
```
_ATL_FREE_THREADED
```  
  
### <a name="remarks"></a>Comentarios  
 Especifica el subprocesamiento libre. Subprocesamiento libre equivale a un modelo de apartamento multiproceso. Vea [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) de otros subprocesos opciones, y [opciones, Asistente para objetos simples de ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos los modelos disponibles para un objeto ATL.  
  
##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED  
 Un símbolo que indica el proyecto tendrá los objetos que están marcados como ambos, libre o Neutral.  
  
```
_ATL_MULTI_THREADED
```  
  
### <a name="remarks"></a>Comentarios  
 Si se define este símbolo, extraerá ATL en el código que se sincronizará correctamente el acceso a los datos globales. Código nuevo debe usar la macro equivalente [_ATL_FREE_THREADED](#_atl_free_threaded) en su lugar.  
  
##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE  
 Un símbolo que impide el uso predeterminado de espacio de nombres como ATL.  
  
```
_ATL_NO_AUTOMATIC_NAMESPACE
```  
  
### <a name="remarks"></a>Comentarios  
 Si no se define este símbolo, incluidos atlbase.h llevará a cabo **con espacio de nombres ATL** de forma predeterminada, lo que puede dar lugar a conflictos de nomenclatura. Para evitar esto, defina este símbolo.  
  
##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT  
 Un símbolo que impide que el código relacionado con COM que se está compilando con el proyecto.  
  
```
_ATL_NO_COM_SUPPORT```  
  
##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE  
 A symbol that prevents the vtable pointer from being initialized in the class's constructor and destructor.  
  
```
ATL_NO_VTABLE
```  
  
### Remarks  
 If the vtable pointer is prevented from being initialized in the class's constructor and destructor, the linker can eliminate the vtable and all of the functions to which it points. Expands to **__declspec(novtable)**.  
  
### Example  
 [!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]  
  
##  <a name="atl_noinline"></a>  ATL_NOINLINE  
 A symbol that indicates a function should not be inlined.  
  
```
    ATL_NOINLINE inline
    myfunction
 { ... }
```  
  
### Parameters  
 *myfunction*  
 The function that should not be inlined.  
  
### Remarks  
 Use this symbol if you want to ensure a function does not get inlined by the compiler, even though it must be declared as inline so that it can be placed in a header file. Expands to **__declspec(noinline)**.  
  
##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED  
 Define if all of your objects use the single threading model  
  
```
_ATL_SINGLE_THREADED
```  
  
### Remarks  
 Specifies that the object always runs in the primary COM thread. See [Specifying the Project's Threading Model](../../atl/specifying-the-threading-model-for-a-project-atl.md) for other threading options, and [Options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
## See Also  
 [Macros](../../atl/reference/atl-macros.md)
