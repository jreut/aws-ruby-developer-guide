.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

.. _aws-ruby-sdk-sqs-recipes:

#############
|SQS| Recipes
#############

This section provides some recipes you can use to access |SQSlong| (|SQS|) using the |sdk-ruby|. For
more information about |SQS|, see the `Amazon SQS documentation <http://aws.amazon.com/documentation/sqs/>`_.

This section contains information about the following recipes:

* :ref:`aws-ruby-sdk-sqs-recipe-show-queues`

* :ref:`aws-ruby-sdk-sqs-recipe-create-queue`

* :ref:`aws-ruby-sdk-sqs-recipe-send-messages`

* :ref:`aws-ruby-sdk-sqs-recipe-get-messages`

* :ref:`aws-ruby-sdk-sqs-recipe-get-messages-with-long-polling`

* :ref:`aws-ruby-sdk-sqs-recipe-poll-messages`

* :ref:`aws-ruby-sdk-sqs-recipe-redirect-deadletters`

* :ref:`aws-ruby-sdk-sqs-recipe-delete_queue`

* :ref:`aws-ruby-sdk-sqs-recipe-enable-resource`

.. _aws-ruby-sdk-sqs-recipe-show-queues:

Getting Information about all Queues
====================================

The following example lists the URLs, ARNs, messages available, and messages in flight of your |SQS| queues in the region :code:`us-west-2`.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-show-queues.rb
   :lines: 13-42
   :dedent: 0
   :language: ruby

.. _aws-ruby-sdk-sqs-recipe-create-queue:

Creating a Queue
================

The following example creates the |SQS| queue :code:`MyGroovyQueue` in the region :code:`us-west-2` and displays its URL.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-create-queue.rb
   :lines: 13-19
   :dedent: 0
   :language: ruby

.. _aws-ruby-sdk-sqs-recipe-send-messages:

Sending Messages
================

The following example sends the message "Hello world" through the |SQS| queue with the URL :code:`URL` in the region :code:`us-west-2`.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-send-message.rb
   :lines: 13-17
   :dedent: 0
   :language: ruby

The following example sends the messages 'Hello world' and 'How is the weather?' through the |SQS| queue
with the URL :code:`URL` in the region :code:`us-west-2` region.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-send-message-batch.rb
   :lines: 13-29
   :dedent: 0
   :language: ruby

.. _aws-ruby-sdk-sqs-recipe-get-messages:

Receiving Messages
==================

The following example displays the body of up to 10 messages in the |SQS| queue with the URL :code:`URL` in the region :code:`us-west-2`.
Note that receive_message does not guarantee to get all messages
(see `Properties of Distributed Queues <http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/DistributedQueues.html>`_),
and by default does not delete the message.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-get-messages.rb
   :lines: 13-21
   :dedent: 0
   :language: ruby

.. _aws-ruby-sdk-sqs-recipe-get-messages-with-long-polling:

Receiving Messages using Long Polling
=====================================

The following example waits up to 10 seconds to display the bodies of up to 10 messages in the |SQS| queue
with the URL :code:`URL` in the region :code:`us-west-2`.
Note that if you do not specify a wait time, the default value is **0** (|SQS| does not wait).

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-get-messages-with-long-polling.rb
   :lines: 13-21
   :dedent: 0
   :language: ruby

.. _aws-ruby-sdk-sqs-recipe-poll-messages:

Receiving Messages using the QueuePoller Class
==============================================

The following example uses the **QueuePoller** utility class to display the body of all messages in the SQS queue
with the URL :code:`URL` in the :code:`us-west-2` region, and deletes the message.
After approximately 15 seconds of inactivity the script times out.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-poll-messages.rb
   :lines: 13-21
   :dedent: 0
   :language: ruby

The following example loops through the |SQS| queue with the URL :code:`URL`, and waits up to *duration* seconds.

You can get the correct URL by executing the |SQS| example in :ref:`aws-ruby-sdk-sqs-recipe-show-queues`.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-long-polling.rb
   :lines: 13-21
   :dedent: 0
   :language: ruby

The following example loops through the |SQS| queue with the URL :code:`URL`,
and gives you up to the visibility *timeout* seconds to process the message, represented by the method *do_something*.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-visibility-timeout.rb
   :lines: 13-26
   :dedent: 0
   :language: ruby

The following example loops through the |SQS| queue with the URL :code:`URL`,
and changes the visibility *timeout* seconds, for any message that needs additional processing by the method :code:`do_something2`

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-visibility-timeout2.rb
   :lines: 13-36
   :dedent: 0
   :language: ruby

.. _aws-ruby-sdk-sqs-recipe-redirect-deadletters:

Redirecting Dead Letters
========================

The following example redirects any dead letters from the queue with the URL *URL* to the queue with the ARN *ARN*.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-redirect-queue-deadletters.rb
   :lines: 13-23
   :dedent: 0
   :language: ruby

.. _aws-ruby-sdk-sqs-recipe-delete_queue:

Deleting a Queue
================

The following example deletes the |SQS| queue with the URL *URL* in the region :code:`us-west-2`.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-delete-queue.rb
   :lines: 13-17
   :dedent: 0
   :language: ruby

.. _aws-ruby-sdk-sqs-recipe-enable-resource:

Enabling a Resource to Publish to a Queue
=========================================

The following example enables the resource with the ARN *my-resource-arn* to publish
to the queue with the ARN *my-queue-arn* and URL *my-queue-url* in the region :code:`us-west-2`.

.. literalinclude:: ../build_dependencies/1/ruby/example_code/sqs/sqs-ruby-example-enable-resource.rb
   :lines: 13-40
   :dedent: 0
   :language: ruby