.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

#############
|LAM| Recipes
#############

You can use the following recipes to access |LAMlong| (|LAM|) using the |sdk-ruby|. For
more information about |LAM|, see the `Lambda documentation <http://aws.amazon.com/documentation/lambda/>`_.

**Recipes**

* :ref:`lambda-ruby-example-show-functions`

* :ref:`lambda-ruby-example-create-function`

* :ref:`lambda-ruby-example-configure-function-for-notification`

.. _lambda-ruby-example-show-functions:

Displaying Information about All |LAM| Functions
================================================

The following example displays the name, ARN, and role of all of your |LAM| functions in the :code:`us-west-2` region.

.. literalinclude:: ./example_code/lambda/aws-ruby-sdk-lambda-example-show-functions.rb
   :lines: 13-21
   :dedent: 0
   :language: ruby

.. _lambda-ruby-example-create-function:

Creating a |LAM| Function
=========================

The following example creates the |LAM| function :code:`my-notification-function` in the :code:`us-west-2` region using these values:

* Role ARN: :code:`my-resource-arn`. In most cases, you need to attach only the :code:`AWSLambdaExecute` managed policy to the policy for this role.
  
* Function entry point: :code:`my-package.my-class`

* Runtime: :code:`java8`

* Zip file: :code:`my-zip-file.zip`

* Bucket: :code:`my-notification-bucket`

* Key: :code:`my-zip-file`

.. literalinclude:: ./example_code/lambda/aws-ruby-sdk-lambda-example-create-function.rb
   :lines: 13-32
   :dedent: 0
   :language: ruby

.. _lambda-ruby-example-configure-function-for-notification:

Configuring a |LAM| Function to Receive Notifications
=====================================================

The following example configures the |LAM| function :code:`my-notification-function` in the :code:`us-west-2` region to accept notifications from the resource with the ARN :code:`my-resource-arn`.

.. literalinclude:: ./example_code/lambda/aws-ruby-sdk-lambda-example-configure-function-for-notification.rb
   :lines: 13-24
   :dedent: 0
   :language: ruby
