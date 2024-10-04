// FAQ Accordion
document.addEventListener('DOMContentLoaded', () => {
  const faqContainer = document.querySelector('.faq-content');

  faqContainer.addEventListener('click', (e) => {
    const groupHeader = e.target.closest('.faq-group-header');
    if (!groupHeader) return;
    // console.log(groupHeader);

    const group = groupHeader.parentElement;
    // console.log(group);
    const groupBody = group.querySelector('.faq-group-body');
    const icon = groupHeader.querySelector('i');
    // console.log(icon);

    // Toggle icon
    icon.classList.toggle('fa-plus');
    icon.classList.toggle('fa-minus');

    // Toggle body visibility
    groupBody.classList.toggle('open');

    // Toggle remove other open bodies
    const otherGroups = faqContainer.querySelectorAll('.faq-group');
    // console.log(otherGroups);
    otherGroups.forEach((otherGroup) => {
      if (otherGroup !== group) {
        const otherGroupBody = otherGroup.querySelector('.faq-group-body');
        const otherIcon = otherGroup.querySelector('.faq-group-header i');

        otherGroupBody.classList.remove('open');
        otherIcon.classList.remove('fa-minus');
        otherIcon.classList.add('fa-plus');
      }
    });
  });
});
