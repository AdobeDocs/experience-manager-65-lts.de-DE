---
title: Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten
description: Erfahren Sie, wie Sie gültige und abgelaufene Zertifikate in PDF-Dokumenten erkennen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 100%

---

# Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten {#recognizing-valid-and-expired-certificates-in-pdf-documents}

Wird ein PDF-Dokument, dem über Reader Extensions Verwendungsrechte zugewiesen wurden, in Adobe Reader geöffnet, wird eine Statusleiste mit den spezifischen Verwendungsrechten angezeigt, die im PDF-Dokument aktiviert sind.

Wenn das digitale Zertifikat mit den für ein PDF-Dokument angegebenen Verwendungsrechten abläuft und das PDF-Dokument in Adobe Reader geöffnet wird, werden die Benutzenden über ein Dialogfeld darauf hingewiesen, dass das PDF-Dokument zwar Verwendungsrechte aufweist, diese jedoch deaktiviert sind. Diese Meldung besagt, dass das PDF-Dokument geändert oder manipuliert wurde. Dies muss jedoch nicht der Fall sein. Adobe Reader zeigt diese Meldung an, wenn das Zertifikat abläuft oder ein Dokument geändert wird. In Adobe Reader 7.0.x oder höher kann nicht festgestellt werden, welcher Fall gerade vorliegt.

Nachdem Sie das Dialogfeld geschlossen haben, öffnet Adobe Reader das PDF-Dokument. Die Verwendungsrechte, die mit den Acrobat Reader DC-Erweiterungen aktiviert wurden, sind wie erwartet nicht verfügbar. Wenn das PDF-Dokument ein interaktives Formular ist, sind die Formularfelder gesperrt, sodass Benutzende die Formulardaten nicht ändern können.
