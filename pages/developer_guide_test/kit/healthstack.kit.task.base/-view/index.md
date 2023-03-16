---
title: View
permalink: /kit/healthstack.kit.task.base/-view/index.html

---
//[kit](../../../index.html)/[healthstack.kit.task.base](../index.html)/[View](index.html)



# View



[androidJvm]\
abstract class [View](index.html)&lt;[T](index.html) : [StepModel](../-step-model/index.html)&gt;

A UI rendering object for [Step](../-step/index.html).



It has composable function [Render](-render.html), which renders UI using data in healthstack.kit.tqask.base.TaskModel.



## Constructors


| | |
|---|---|
| [View](-view.html) | [androidJvm]<br>fun [View](-view.html)() |


## Functions


| Name | Summary |
|---|---|
| [Render](-render.html) | [androidJvm]<br>@Composable<br>abstract fun [Render](-render.html)(model: [T](index.html), callbackCollection: [CallbackCollection](../-callback-collection/index.html), holder: [SubStepHolder](../../healthstack.kit.task.survey.question/-sub-step-holder/index.html)?)<br>A method rendering UI. |


## Inheritors


| Name |
|---|
| [TappingSpeedIntroView](../../healthstack.kit.task.activity.view/-tapping-speed-intro-view/index.html) |
| [TappingSpeedMeasureView](../../healthstack.kit.task.activity.view/-tapping-speed-measure-view/index.html) |
| [TappingSpeedResultView](../../healthstack.kit.task.activity.view/-tapping-speed-result-view/index.html) |
| [SimpleActivityView](../../healthstack.kit.task.activity.view.common/-simple-activity-view/index.html) |
| [ConsentTextView](../../healthstack.kit.task.onboarding.view/-consent-text-view/index.html) |
| [EligibilityIntroView](../../healthstack.kit.task.onboarding.view/-eligibility-intro-view/index.html) |
| [EligibilityResultView](../../healthstack.kit.task.onboarding.view/-eligibility-result-view/index.html) |
| [IntroView](../../healthstack.kit.task.onboarding.view/-intro-view/index.html) |
| [RegistrationCompletedView](../../healthstack.kit.task.signup.view/-registration-completed-view/index.html) |
| [SignUpView](../../healthstack.kit.task.signup.view/-sign-up-view/index.html) |
| [SurveyView](../../healthstack.kit.task.survey.view/-survey-view/index.html) |

