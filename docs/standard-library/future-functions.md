---
title: '&lt;future&gt; (Funciones) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: c542e696e0e5ddef350d40b45fe16f4c3a77882d
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="ltfuturegt-functions"></a>&lt;future&gt; (Funciones)
||||  
|-|-|-|  
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|  
|[make_error_condition](#make_error_condition)|[swap](#swap)|  
  
##  <a name="async"></a>  async  
 Representa un *proveedor asincrónico*.  
  
```
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```  
  
### <a name="parameters"></a>Parámetros  
 `policy`  
 Valor [launch](../standard-library/future-enums.md#launch).  
  
### <a name="remarks"></a>Comentarios  
 Definiciones de las abreviaturas:  
  
|||  
|-|-|  
|*dfn*|Resultado de llamar a `decay_copy(forward<Fn>(fn))`.|  
|*dargs*|Resultado de las llamadas `decay_copy(forward<ArgsTypes>(args...))`.|  
|*Ty*|El tipo `result_of<Fn(ArgTypes...)>::type`.|  
  
 La primera función de plantilla devuelve `async(launch::any, fn, args...)`.  
  
 La segunda función devuelve un objeto `future<Ty>` cuyo *estado asincrónico asociado* contiene un resultado junto con los valores de *dfn* y *dargs* y un objeto de subproceso para administrar un subproceso de ejecución independiente.  
  
 A menos que `decay<Fn>::type` sea un tipo distinto de launch, la segunda función no participa en la resolución de sobrecarga.  
  
 Si `policy` es `launch::any`, la función puede elegir `launch::async` o `launch::deferred`. En esta implementación, la función utiliza `launch::async`.  
  
 Si `policy` es `launch::async`, la función crea un subproceso que evalúa `INVOKE(dfn, dargs..., Ty)`. La función vuelve después de crear el subproceso sin esperar los resultados. Si el sistema no puede iniciar un nuevo subproceso, la función produce un [system_error](../standard-library/system-error-class.md) que tiene un código de error de `resource_unavailable_try_again`.  
  
 Si `policy` es `launch::deferred`, la función marca su estado asincrónico asociado como que contiene una *función aplazada* y vuelve. La primera llamada a cualquier función no cronometrada que espera hasta que el estado asincrónico asociado esté listo llama a la función aplazada evaluando `INVOKE(dfn, dargs..., Ty)`.  
  
 En todos los casos, el estado asincrónico asociado del objeto `future` no se establece en *listo* hasta que la evaluación de `INVOKE(dfn, dargs..., Ty)` no se completa, ya sea iniciando una excepción o volviendo normalmente. El resultado del estado asincrónico asociado es una excepción si se produjo alguna, o cualquier valor devuelto por la evaluación.  
  
> [!NOTE]
>  Para un `future` (o el último [shared_future](../standard-library/shared-future-class.md)) adjunto a una tarea iniciada con `std::async`, el destructor se bloquea si la tarea no se ha completado; es decir, se bloquea si este subproceso aún no ha llamado a `.get()` o `.wait()` y la tarea todavía se está ejecutando. Si un `future` obtenido de `std::async` se desplaza fuera del ámbito local, otro código que lo utilice debe saber que su destructor se puede bloquear para que el estado compartido se convierta en listo.  
  
 La pseudofunción `INVOKE` se define en [\<functional>](../standard-library/functional.md).  
  
##  <a name="future_category"></a>  future_category  
 Devuelve una referencia al objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores asociados a objetos `future`.  
  
```
const error_category& future_category() noexcept;
```  
  
##  <a name="make_error_code"></a>  make_error_code  
 Crea un [error_code](../standard-library/error-code-class.md) junto con el objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores de [future](../standard-library/future-class.md).  
  
```
inline error_code make_error_code(future_errc Errno) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Errno`  
 Valor [future_errc](../standard-library/future-enums.md#future_errc) que identifica el error notificado.  
  
### <a name="return-value"></a>Valor devuelto  
 `error_code(static_cast<int>(Errno), future_category());`  
  
##  <a name="make_error_condition"></a>  make_error_condition  
 Crea una [error_condition](../standard-library/error-condition-class.md) junto con el objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores de [future](../standard-library/future-class.md).  
  
```
inline error_condition make_error_condition(future_errc Errno) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Errno`  
 Valor [future_errc](../standard-library/future-enums.md#future_errc) que identifica el error notificado.  
  
### <a name="return-value"></a>Valor devuelto  
 `error_condition(static_cast<int>(Errno), future_category());`  
  
##  <a name="swap"></a>  swap  
 Intercambia el *estado asincrónico asociado* de un objeto `promise` con el de otro.  
  
```
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `promise` izquierdo.  
  
 `Right`  
 Objeto `promise` derecho.  
  
## <a name="see-also"></a>Vea también  
 [\<future>](../standard-library/future.md)




