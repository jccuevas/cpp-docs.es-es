---
title: 'Multithreading: Finalizar subprocesos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
dev_langs:
- C++
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdf9376e9f8c9e9d74d88d0bef40dc71fd43d51f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-terminating-threads"></a>Multithreading: Finalizar subprocesos
Dos situaciones normales que un subproceso terminar: la función controladora finaliza o el subproceso no puede ejecutarse hasta su finalización. Si un procesador de textos, se utiliza un subproceso para impresión en segundo plano, la función controladora terminaría normalmente si la impresión se completa correctamente. Si el usuario desea cancelar la impresión, sin embargo, el subproceso en segundo plano impresión tiene finalizó de forma prematura. Este tema explica cómo implementar cada situación y cómo obtener el código de salida de un subproceso después de que termine.  
  
-   [Terminación normal de subproceso](#_core_normal_thread_termination)  
  
-   [Terminación prematura de subprocesos](#_core_premature_thread_termination)  
  
-   [Recuperar el código de salida de un subproceso](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> Terminación normal de subproceso  
 Para un subproceso de trabajo, la terminación normal de subproceso es simple: salir de la función controladora y devolver un valor que indica la razón de finalización. Puede usar el [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) función o un `return` instrucción. Normalmente, 0 significa terminación sin error, pero que depende de usted.  
  
 Para un subproceso de interfaz de usuario, el proceso es simple: desde el subproceso de interfaz de usuario, debe llamar a [función PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945) en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. El único parámetro que **función PostQuitMessage** toma es el código de salida del subproceso. Para subprocesos de trabajo, 0 suele significar finalización correcta.  
  
##  <a name="_core_premature_thread_termination"></a> Terminación prematura de subprocesos  
 Finaliza un subproceso de forma prematura es casi tan sencillo: llamar a [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) desde dentro del subproceso. Pase el código de salida deseado como único parámetro. Esto detiene la ejecución del subproceso, cancela la asignación de la pila del subproceso, desasocia todos los archivos DLL que se adjunta al subproceso y elimina el objeto de subproceso de la memoria.  
  
 `AfxEndThread` Se debe invocar desde dentro del subproceso que debe finalizar. Si desea terminar un subproceso desde otro subproceso, debe configurar un método de comunicación entre los dos subprocesos.  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> Recuperar el código de salida de un subproceso  
 Para obtener el código de salida del trabajo o el subproceso de interfaz de usuario, llame a la [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190) función. Para obtener información acerca de esta función, vea la [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Esta función recibe el identificador del subproceso (almacenado en el `m_hThread` miembro de datos de `CWinThread` objetos) y la dirección de un `DWORD`.  
  
 Si el subproceso está aún activo, **GetExitCodeThread** coloca **STILL_ACTIVE** en proporcionado `DWORD` dirección; de lo contrario, el código de salida se coloca en esta dirección.  
  
 Recuperar el código de salida [CWinThread](../mfc/reference/cwinthread-class.md) objetos requiere un paso adicional. De forma predeterminada, cuando un `CWinThread` subproceso finaliza, se elimina el objeto de subproceso. Esto significa que no se puede obtener acceso a la `m_hThread` miembro de datos porque la `CWinThread` objeto ya no existe. Para evitar esta situación, realice una de las siguientes acciones:  
  
-   Establecer el `m_bAutoDelete` miembro de datos **FALSE**. Esto permite la `CWinThread` objeto sobreviva después de que el subproceso ha terminado. A continuación, puede tener acceso a la `m_hThread` miembro de datos después de que el subproceso ha terminado. Si utiliza esta técnica, sin embargo, usted es responsable de destruir la `CWinThread` objeto porque el marco de trabajo no lo eliminará automáticamente. Este es el método preferido.  
  
-   Almacenar el identificador del subproceso de forma independiente. Después de crea el subproceso, copie su `m_hThread` miembro de datos (mediante **:: DuplicateHandle**) a otra variable y tener acceso a él a través de esa variable. Esta forma, el objeto se elimina automáticamente cuando se produce la finalización y aún puede averiguar por qué el subproceso ha terminado. Asegúrese de que el subproceso no termina antes de poder duplicar el identificador. La forma más segura de hacerlo consiste en pasar **CREATE_SUSPENDED** a [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), almacenar el identificador y, a continuación, reanudar el subproceso mediante una llamada a [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).  
  
 Cualquiera de los métodos permite determinar por qué un `CWinThread` objeto terminada.  
  
## <a name="see-also"></a>Vea también  
 [Subprocesamiento múltiple con C++ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)   
 [_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
 [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)