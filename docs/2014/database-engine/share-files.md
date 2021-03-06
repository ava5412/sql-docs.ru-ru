---
title: Общий доступ к файлам | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b931d9ebcf8ef5889158a4c393833298dc3b097a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308084"
---
# <a name="share-files"></a>Открытие файлов для общего доступа
  В [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] можно открывать общий доступ к элементам проектов управления версиями. При совместном использовании элемента все производимые в нем изменения отображаются во всех проектах, для которых открыт общий доступ к данному элементу.  
  
 Общий доступ к элементам обеспечивает следующие преимущества для пользователей системы управления версиями.  
  
-   Отпадает необходимость хранить отдельную копию общего элемента для каждого проекта, в котором он используется. Это позволяет экономить место на диске как на клиенте, так и на сервере управления версиями. Поставщик управления версиями хранит общий элемент в одном централизованном месте, а каждый проект, имеющий доступ к элементу, содержит указатель на это место.  
  
-   Предотвращается несовместимость версий. Так как каждый проект, который использует элемент, работает с одной и той же версией элемента, предотвращается возможность конфликтов в случае изменения элемента несколькими проектами независимо друг от друга.  
  
### <a name="to-share-an-item"></a>Открытие общего доступа к элементу  
  
1.  В обозревателе решений выберите папку или проект, в которых необходимо разместить файлы общего доступа.  
  
2.  На **файл** последовательно выберите пункты **системы управления версиями**, а затем нажмите кнопку **общего ресурса**.  
  
3.  В **совместное использование с** диалоговом окне Список папок для элемента, нужно предоставить общий доступ и щелкните этот элемент.  
  
4.  Нажмите кнопку **общего ресурса**.  
  
## <a name="see-also"></a>См. также  
 [Основы системы управления версиями](../../2014/database-engine/source-control-basics.md)  
  
  
