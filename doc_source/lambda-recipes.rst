.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

.. _aws-ruby-sdk-lambda-recipes:

#############
|LAM| Recipes
#############

This section provides some recipes you can use to access |LAMlong| (|LAM|) using the |sdk-ruby|. For
more information about |LAM|, see the `Lambda documentation <http://aws.amazon.com/documentation/lambda/>`_.

This section contains the following recipes:

* :ref:`lambda-ruby-example-show-functions`

* :ref:`lambda-ruby-example-create-function`

* :ref:`lambda-ruby-example-configure-function-for-notification`

.. _lambda-ruby-example-show-functions:

Displaying Information about all |LAM| Functions
================================================

The following example displays the name, ARN, and role of all of your |LAM| functions in the region :code:`us-west-2`

.. literalinclude:: ../build_dependencies/1/ruby/example_code/lambda/aws-ruby-sdk-lambda-example-show-functions.rb
   :lines: 13-21
   :dedent: 0
   :language: ruby

.. _lambda-ruby-example-create-function:

Creating a |LAM| Function
=========================

The following example creates the |LAM| function :code:`my-notification-function` in the region :code:`us-west-2`

* The role ARN :code:`my-resource-arn`. In most cases you need only attach the :code:`AWSLambdaExecute` managed policy to the policy for this role.
  
* The function entry point :code:`my-package.my-class`

* The runtime :code:`java8`

* The the zip file :code:`my-zip-file.zip`

* The bucket :code:`my-notification-bucket`

* The key :code:`my-zip-file`

.. literalinclude:: ../build_dependencies/1/ruby/example_code/lambda/aws-ruby-sdk-lambda-example-create-function.rb
   :lines: 13-32
   :dedent: 0
   :language: ruby

.. _lambda-ruby-example-configure-function-for-notification:

Configuring a |LAM| Function to Receive Notifications
=====================================================

The following example configures the Lambda function :code:`my-notification-function` in the region :code:`us-west-2` accept notifications from the resource with the ARN :code:`my-resource-arn`:

.. literalinclude:: ../build_dependencies/1/ruby/example_code/lambda/aws-ruby-sdk-lambda-example-configure-function-for-notification.rb
   :lines: 13-24
   :dedent: 0
   :language: ruby