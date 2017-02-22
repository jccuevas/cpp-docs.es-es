---
title: "CAnimationController (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationController"
  - "afxanimationcontroller/CAnimationController"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationController (clase)"
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CAnimationController (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa el controlador de animación, que proporciona una interfaz central para crear y administrar las animaciones.  
  
## Sintaxis  
  
```  
class CAnimationController : public CObject;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationController::CAnimationController](../Topic/CAnimationController::CAnimationController.md)|Construye un controlador de animación.|  
|[CAnimationController::~CAnimationController](../Topic/CAnimationController::~CAnimationController.md)|El destructor.  Se llama cuando se destruye un objeto de controlador de animación.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationController::AddAnimationObject](../Topic/CAnimationController::AddAnimationObject.md)|Agrega un objeto de animación a un grupo que pertenece al controlador de animación.|  
|[CAnimationController::AddKeyframeToGroup](../Topic/CAnimationController::AddKeyframeToGroup.md)|Agrega un fotograma clave a un grupo.|  
|[CAnimationController::AnimateGroup](../Topic/CAnimationController::AnimateGroup.md)|Prepara a un grupo para ejecutar la animación y, opcionalmente, programarla.|  
|[CAnimationController::CleanUpGroup](../Topic/CAnimationController::CleanUpGroup.md)|Sobrecargado.  Lo llama el marco para limpiar el grupo cuando se ha programado la animación.|  
|[CAnimationController::CreateKeyframe](../Topic/CAnimationController::CreateKeyframe.md)|Sobrecargado.  Crea un fotograma clave que depende de la transición y lo agrega al grupo especificado.|  
|[CAnimationController::EnableAnimationManagerEvent](../Topic/CAnimationController::EnableAnimationManagerEvent.md)|Establece o libera un controlador para llamar cuando cambia el estado del administrador de animaciones.|  
|[CAnimationController::EnableAnimationTimerEventHandler](../Topic/CAnimationController::EnableAnimationTimerEventHandler.md)|Establece o libera un controlador para sincronizar eventos y un controlador para sincronizar las actualizaciones.|  
|[CAnimationController::EnablePriorityComparisonHandler](../Topic/CAnimationController::EnablePriorityComparisonHandler.md)|Establece o libera el controlador de comparación de prioridad para llamar y determinar si un guión gráfico programado se puede cancelar, concluir, recortar o comprimir.|  
|[CAnimationController::EnableStoryboardEventHandler](../Topic/CAnimationController::EnableStoryboardEventHandler.md)|Establece o libera un controlador para el estado del guión gráfico y eventos de actualización.|  
|[CAnimationController::FindAnimationGroup](../Topic/CAnimationController::FindAnimationGroup.md)|Sobrecargado.  Encuentra un grupo de animación por su guión gráfico.|  
|[CAnimationController::FindAnimationObject](../Topic/CAnimationController::FindAnimationObject.md)|Encuentra el objeto de animación que contiene una variable de animación especificada.|  
|[CAnimationController::GetKeyframeStoryboardStart](../Topic/CAnimationController::GetKeyframeStoryboardStart.md)|Devuelve un fotograma clave que identifica el inicio de guión gráfico.|  
|[CAnimationController::GetUIAnimationManager](../Topic/CAnimationController::GetUIAnimationManager.md)|Proporciona acceso para encapsular el objeto IUIAnimationManager.|  
|[CAnimationController::GetUIAnimationTimer](../Topic/CAnimationController::GetUIAnimationTimer.md)|Proporciona acceso para encapsular el objeto IUIAnimationTimer.|  
|[CAnimationController::GetUITransitionFactory](../Topic/CAnimationController::GetUITransitionFactory.md)|Un puntero a la interfaz IUIAnimationTransitionFactory o NULL, si se produjera un error en la creación de la biblioteca de transiciones.|  
|[CAnimationController::GetUITransitionLibrary](../Topic/CAnimationController::GetUITransitionLibrary.md)|Proporciona acceso para encapsular el objeto IUIAnimationTransitionLibrary.|  
|[CAnimationController::IsAnimationInProgress](../Topic/CAnimationController::IsAnimationInProgress.md)|Indica si por lo menos un grupo está reproduciendo la animación.|  
|[CAnimationController::IsValid](../Topic/CAnimationController::IsValid.md)|Indica si el controlador de animación es válido.|  
|[CAnimationController::OnAnimationIntegerValueChanged](../Topic/CAnimationController::OnAnimationIntegerValueChanged.md)|Lo llama el marco cuando el valor entero de la variable de animación ha cambiado.|  
|[CAnimationController::OnAnimationManagerStatusChanged](../Topic/CAnimationController::OnAnimationManagerStatusChanged.md)|Lo llama el marco en respuesta al evento StatusChanged del administrador de animaciones.|  
|[CAnimationController::OnAnimationTimerPostUpdate](../Topic/CAnimationController::OnAnimationTimerPostUpdate.md)|Lo llama el marco una vez finalizada una actualización de animación.|  
|[CAnimationController::OnAnimationTimerPreUpdate](../Topic/CAnimationController::OnAnimationTimerPreUpdate.md)|Lo llama el marco antes del comienzo de una actualización de animación.|  
|[CAnimationController::OnAnimationTimerRenderingTooSlow](../Topic/CAnimationController::OnAnimationTimerRenderingTooSlow.md)|Llamado por el marco cuando la velocidad de fotogramas de representación para una animación cae por debajo de una velocidad de fotogramas mínima deseable.|  
|[CAnimationController::OnAnimationValueChanged](../Topic/CAnimationController::OnAnimationValueChanged.md)|Lo llama el marco cuando el valor de la variable de animación ha cambiado.|  
|[CAnimationController::OnBeforeAnimationStart](../Topic/CAnimationController::OnBeforeAnimationStart.md)|Lo llama el marco justo antes de que se programe la animación.|  
|[CAnimationController::OnHasPriorityCancel](../Topic/CAnimationController::OnHasPriorityCancel.md)|Llamado por el marco para resolver los conflictos de programación.|  
|[CAnimationController::OnHasPriorityCompress](../Topic/CAnimationController::OnHasPriorityCompress.md)|Llamado por el marco para resolver los conflictos de programación.|  
|[CAnimationController::OnHasPriorityConclude](../Topic/CAnimationController::OnHasPriorityConclude.md)|Llamado por el marco para resolver los conflictos de programación.|  
|[CAnimationController::OnHasPriorityTrim](../Topic/CAnimationController::OnHasPriorityTrim.md)|Llamado por el marco para resolver los conflictos de programación.|  
|[CAnimationController::OnStoryboardStatusChanged](../Topic/CAnimationController::OnStoryboardStatusChanged.md)|Lo llama el marco cuando el estado del guión gráfico ha cambiado.|  
|[CAnimationController::OnStoryboardUpdated](../Topic/CAnimationController::OnStoryboardUpdated.md)|Lo llama el marco cuando el guión gráfico se ha actualizado.|  
|[CAnimationController::RemoveAllAnimationGroups](../Topic/CAnimationController::RemoveAllAnimationGroups.md)|Quita todos los grupos de animación del controlador de animación.|  
|[CAnimationController::RemoveAnimationGroup](../Topic/CAnimationController::RemoveAnimationGroup.md)|Quita un grupo de animación con el id. especificado del controlador de animación.|  
|[CAnimationController::RemoveAnimationObject](../Topic/CAnimationController::RemoveAnimationObject.md)|Quite un objeto de animación del controlador de animación.|  
|[CAnimationController::RemoveTransitions](../Topic/CAnimationController::RemoveTransitions.md)|Quita las transiciones de los objetos de animación que pertenecen al grupo especificado.|  
|[CAnimationController::ScheduleGroup](../Topic/CAnimationController::ScheduleGroup.md)|Programa una animación.|  
|[CAnimationController::SetRelatedWnd](../Topic/CAnimationController::SetRelatedWnd.md)|Establece una relación entre el controlador de animación y una ventana.|  
|[CAnimationController::UpdateAnimationManager](../Topic/CAnimationController::UpdateAnimationManager.md)|Dirige el administrador de animaciones para actualizar los valores de todas las variables de animación.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationController::CleanUpGroup](../Topic/CAnimationController::CleanUpGroup.md)|Sobrecargado.  Una aplicación auxiliar que limpia el grupo.|  
|[CAnimationController::OnAfterSchedule](../Topic/CAnimationController::OnAfterSchedule.md)|Lo llama el marco cuando solo se ha programado una animación para el grupo especificado.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationController::g\_KeyframeStoryboardStart](../Topic/CAnimationController::g_KeyframeStoryboardStart.md)|Un fotograma clave que representa el inicio de guión gráfico.|  
|[CAnimationController::m\_bIsValid](../Topic/CAnimationController::m_bIsValid.md)|Especifica si un controlador de animación es válido o no.  Este miembro está establecido en FALSE si el SO actual no admite la API de Windows Animation.|  
|[CAnimationController::m\_lstAnimationGroups](../Topic/CAnimationController::m_lstAnimationGroups.md)|Una lista de grupos de animación que pertenece a este controlador de animación.|  
|[CAnimationController::m\_pAnimationManager](../Topic/CAnimationController::m_pAnimationManager.md)|Almacena un puntero al objeto COM del administrador de animaciones.|  
|[CAnimationController::m\_pAnimationTimer](../Topic/CAnimationController::m_pAnimationTimer.md)|Almacena un puntero al objeto COM del temporizador de animaciones.|  
|[CAnimationController::m\_pRelatedWnd](../Topic/CAnimationController::m_pRelatedWnd.md)|Un puntero a un objeto CWnd relacionado, que se puede dibujar de nuevo automáticamente cuando el estado del administrador de animaciones ha cambiado o se ha producido un evento de actualización posterior.  Puede ser NULL.|  
|[CAnimationController::m\_pTransitionFactory](../Topic/CAnimationController::m_pTransitionFactory.md)|Almacena un puntero al objeto COM de generador de transiciones.|  
|[CAnimationController::m\_pTransitionLibrary](../Topic/CAnimationController::m_pTransitionLibrary.md)|Almacena un puntero al objeto COM de la biblioteca de transiciones.|  
  
## Comentarios  
 La clase CAnimationController es la clase clave que administra las animaciones.  Puede crear una o más instancias de controlador de animación en una aplicación y, opcionalmente, conectar una instancia de controlador de animación a un objeto CWnd mediante CAnimationController::SetRelatedWnd.  Esta conexión es necesaria para enviar automáticamente los mensajes WM\_PAINT a la ventana relacionada cuando el estado del administrador de animaciones ha cambiado o el temporizador de animaciones se ha actualizado.  Si no habilita esta relación, debe actualizar de forma manual una ventana que muestra una animación.  Para este propósito, puede derivar una clase de CAnimationController e invalidar OnAnimationManagerStatusChanged u OnAnimationTimerPostUpdate, además de invalidar una o más ventanas cuando sea necesario.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationController](../../mfc/reference/canimationcontroller-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)