---
title: Macros de opciones del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: dbce962873194c1bdcb063537247650cff568e35
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-options-macros"></a>Macros de opciones del compilador
Estas macros controlan características específicas del compilador.  
  
|||  
|-|-|  
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Convierte un símbolo que habilita los errores en los proyectos de versiones anteriores de ATL.|  
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Define si uno o varios de los objetos utilizan el subprocesamiento controlado.|  
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Se asegura de `CString` constructores explícitos, lo que impide cualquier conversión involuntaria.|  
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Definir esta macro con el fin de utilizar estándar compatible con sintaxis de C++, que genera el error del compilador C4867 cuando se utiliza una sintaxis no estándar para inicializar un puntero a una función miembro.|  
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Define si uno o varios de los objetos utilizan el subprocesamiento libre o neutral.|  
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Un símbolo que indica el proyecto tendrá los objetos que están marcados como ambos libre o Neutral. La macro [_ATL_FREE_THREADED](#_atl_free_threaded) debe usarse en su lugar.|  
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Un símbolo que impide el uso predeterminado de espacio de nombres como ATL.|  
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Símbolo que impide que el código relacionado con COM que se compile con el proyecto.|  
|[ATL_NO_VTABLE](#atl_no_vtable)|Símbolo que impide que el puntero vtable que se inicializa en el constructor y el destructor de la clase.|  
|[ATL_NOINLINE](#atl_noinline)|Un símbolo que indica una función no debe estar entre línea.|  
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Define si todos los objetos utilizan el modelo de subprocesamiento único.|  
  
##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS  
 Convierte un símbolo que habilita los errores en los proyectos de versiones anteriores de ATL.  
  
```
#define _ATL_ALL_WARNINGS
```  
  
### <a name="remarks"></a>Comentarios  
 Antes de Visual C++ .NET 2002, ATL había deshabilitado una gran cantidad de advertencias y dejó deshabilitado para que nunca se mostraron en código de usuario. De manera específica:  
  
-   C4127 de expresión condicional es constante  
  
-   C4786 'identificador': identificador se ha truncado a 'número' caracteres en la información de depuración  
  
-   C4201 ha utilizado una extensión no estándar: struct/union sin nombre  
  
-   C4103 'nombredearchivo': utilizado #pragma pack para cambiar la alineación  
  
-   C4291 'declaración': ningún operador delete que coincida se encuentra; no se liberará memoria si la inicialización produce una excepción  
  
-   C4268 'identificador': los datos estáticos/globales 'const' inicializados con el constructor de predeterminado generado por compilador rellenan el objeto con ceros  
  
-   Código de advertencia C4702 inaccesible  
  
 En los proyectos convertidos a partir de versiones anteriores, estas advertencias todavía están deshabilitadas de los encabezados de las bibliotecas.  
  
 Agregando la siguiente línea al archivo stdafx.h antes de incluir los encabezados de las bibliotecas, se puede cambiar este comportamiento.  
  
 [!code-cpp[NVC_ATL_Utilities&#97;](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]  
  
 Si este `#define` se agregan los encabezados ATL son cuidados de conservar el estado de estas advertencias para que no está deshabilitados globalmente (o el usuario deshabilita de forma explícita las advertencias individuales, no para habilitarlos).  
  
 Nuevos proyectos generados con Visual C++ .NET 2002 tendrán este `#define` predeterminada se establece en stdafx.h.  
  
##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED  
 Define si uno o varios de los objetos utilizan el subprocesamiento controlado.  
  
```
_ATL_APARTMENT_THREADED
```  
  
### <a name="remarks"></a>Comentarios  
 Especifica el subproceso de apartamento. Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) de otros subprocesos opciones, y [opciones, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos de modelos disponibles para un objeto ATL.  
  
##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS  
 Se asegura de `CString` constructores explícitos, lo que impide cualquier conversión involuntaria.  
  
```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se define, se compilan todos los constructores de CString que toman un único parámetro con la palabra clave explícita, lo que evita que las conversiones implícitas de argumentos de entrada. Esto significa, por ejemplo, que cuando se define _UNICODE, si intenta usar una char * cadena como argumento de constructor CString, se producirá un error del compilador. Use esta macro en situaciones donde es necesario para evitar conversiones implícitas entre los tipos de cadena estrecho y ancho.  
  
 Al utilizar la macro _T en todos los argumentos de cadena de constructor, puede definir _ATL_CSTRING_EXPLICIT_CONSTRUCTORS y evitar errores de compilación, independientemente de si se ha definido _UNICODE.  
  
##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING  
 Definir esta macro con el fin de forzar el uso de sintaxis compatibles con el estándar de C++ de ANSI para el puntero a las funciones miembro. Utilizando esta macro provocará el error del compilador C4867 generarse cuando se utilizan la sintaxis estándar para inicializar un puntero a una función miembro.  
  
```
#define _ATL_ENABLE_PTM_WARNING
```  
  
### <a name="remarks"></a>Comentarios  
 Las bibliotecas ATL y MFC se han cambiado para coincidir con la compatibilidad de C++ estándar mejorada del compilador de Visual C++. Según el estándar ANSI C++, la sintaxis de un puntero a una función miembro de clase debe ser `&CMyClass::MyFunc`.  
  
 Cuando [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) no está definido (el caso predeterminado), ATL y MFC deshabilita el error C4867 en mapas de macros (mapas de mensajes en particular) para que el código que se creó en versiones anteriores puede seguirán compilándose como antes. Si define **_ATL_ENABLE_PTM_WARNING**, su código debería ser compatible con estándar de C++.  
  
 Sin embargo, el formulario no estándar está desusado, por lo que necesitará mover código existente a la sintaxis compatible con estándar de C++. Por ejemplo, lo siguiente:  
  
 [!code-cpp[NVC_MFCListView&#14;](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]  
  
 Debe cambiarse a:  
  
 [!code-cpp[NVC_MFCListView&#11;](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]  
  
 Tenga en cuenta que para las macros de mapa que agregar el carácter 'aspecto', no debe agregarlo nuevo en el código.  
  
##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED  
 Define si uno o varios de los objetos utilizan el subprocesamiento libre o neutral.  
  
```
_ATL_FREE_THREADED
```  
  
### <a name="remarks"></a>Comentarios  
 Especifica el subprocesamiento libre. Subprocesamiento libre equivale a un modelo de apartamento multiproceso. Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) de otros subprocesos opciones, y [opciones, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos de modelos disponibles para un objeto ATL.  
  
##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED  
 Un símbolo que indica el proyecto tendrá los objetos que están marcados como ambos libre o Neutral.  
  
```
_ATL_MULTI_THREADED
```  
  
### <a name="remarks"></a>Comentarios  
 Si se define este símbolo, ATL extraerá en código que se sincronizará correctamente el acceso a los datos globales. Nuevo código debe utilizar la macro equivalente [_ATL_FREE_THREADED](#_atl_free_threaded) en su lugar.  
  
##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE  
 Un símbolo que impide el uso predeterminado de espacio de nombres como ATL.  
  
```
_ATL_NO_AUTOMATIC_NAMESPACE
```  
  
### <a name="remarks"></a>Comentarios  
 Si no se define este símbolo, incluidos atlbase.h realizará **utilizando el espacio de nombres ATL** de forma predeterminada, lo que puede dar lugar a conflictos de nomenclatura. Para evitar esto, defina este símbolo.  
  
##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT  
 Símbolo que impide que el código relacionado con COM que se compile con el proyecto.  
  
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

